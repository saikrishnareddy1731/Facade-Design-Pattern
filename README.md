# Facade Design Pattern in Java

## Overview

The **Facade Pattern** is a **structural design pattern** that provides a simplified interface to a complex subsystem. It defines a higher-level interface that makes the subsystem easier to use for clients, hiding the complexity behind a single entry point.

### Key Points

- Provides a **unified interface** to a set of interfaces in a subsystem.
- Simplifies usage for clients by hiding complex interactions.
- Promotes **loose coupling** between client code and subsystems.
- Useful when a system has **complex workflows** and the client needs a simple entry point.

### Real-world Example

Consider placing an order on **Zomato**:

1. Customer sees the menu and places an order.
2. Restaurant receives the order and prepares it.
3. Delivery team assigns a delivery boy.
4. Delivery boy picks up and delivers the order.

Without a facade, the client would have to interact with **Restaurant, DeliveryTeam, and DeliveryBoy** separately.  
The **ZomatoFacade** provides a **single method (`placeOrder`)** to handle the entire workflow.

---

## Components of Facade Pattern

1. **Subsystem Classes:** Implement the real work (e.g., `Restaurant`, `DeliveryTeam`, `DeliveryBoy`).
2. **Facade Class:** Provides a simplified interface to the client (`ZomatoFacade`).
3. **Client:** Interacts only with the facade (`Main`).

---

## UML Diagram

```mermaid
classDiagram
    direction LR

    Main --> ZomatoFacade : uses
    ZomatoFacade --> Restaurant : interacts
    ZomatoFacade --> DeliveryTeam : interacts
    ZomatoFacade --> DeliveryBoy : interacts

    class Restaurant {
        +prepareOrder()
    }

    class DeliveryTeam {
        +assignDeliveryBoy()
    }

    class DeliveryBoy {
        +pickUpOrder()
        +deliverOrder()
    }

    class ZomatoFacade {
        -restaurant: Restaurant
        -deliveryTeam: DeliveryTeam
        -deliveryBoy: DeliveryBoy
        +placeOrder()
    }

    class Main {
        +main()
    }
