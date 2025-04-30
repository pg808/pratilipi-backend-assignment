# pratilipi-backend-assignment
# Backend system for personalized notifications
# Personalized Notification System

This project implements a personalized notification system for an e-commerce platform. The system is built using microservices architecture and includes:

- **User Service**: Manages user data and preferences.
- **Notification Service**: Handles the sending and managing of notifications.
- **Recommender Service**: Provides personalized product recommendations.
- **GraphQL Gateway**: A unified API gateway to interact with all services.

## 🏗️ Architecture Overview

The system is composed of several microservices, each running in its own Docker container. The services communicate with each other via RabbitMQ for asynchronous messaging and PostgreSQL for data storage.

### Core Services

1. **User Service**: 
   - Handles user registration, updating preferences, and fetching user details.
   - Communicates with the User PostgreSQL database.
   - Sends events to RabbitMQ to notify other services of changes to user data.

2. **Notification Service**:
   - Manages notifications (e.g., promotions, order updates, recommendations).
   - Stores notifications in the Notification PostgreSQL database.
   - Listens to RabbitMQ events to send notifications based on user actions.

3. **Recommender Service**:
   - Generates personalized product recommendations for users.
   - Consumes user activity and purchase history to provide relevant recommendations.
   - Stores the recommendations in the Recommender PostgreSQL database.

4. **GraphQL Gateway**:
   - Exposes a unified GraphQL API to the client.
   - Aggregates data from all services (User, Notification, Recommender).
   - Uses environment variables to connect to the individual services.

### Message Broker & Database

- **RabbitMQ**: Used for event-driven communication between the services. The system uses RabbitMQ to handle events like user activity, product recommendations, and notifications.
- **PostgreSQL**: Each service has its own PostgreSQL database:
  - `user-db` for the User Service.
  - `notif-db` for the Notification Service.
  - `reco-db` for the Recommender Service.

---

## ⚙️ Getting Started

### Prerequisites

Before running the application, ensure you have the following installed:
- **Docker**: To containerize the microservices and run them locally.
- **Docker Compose**: To orchestrate the multi-container setup.

### Steps to Run the Project Locally

1. Clone the repository:
   ```bash
   git clone <repo-url>
   cd <repo-folder>
2.Github Link - https://github.com/pg808/pratilipi-backend-assignment
