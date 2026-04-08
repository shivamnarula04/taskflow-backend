# TaskFlow Backend

A RESTful API for a task management application built with Java Spring Boot and PostgreSQL.

## Tech Stack

- **Java 17** + **Spring Boot 4**
- **PostgreSQL** — relational database
- **Spring Data JPA / Hibernate** — ORM for database interaction
- **Spring Security** — authentication foundation
- **Maven** — dependency management

## Features

- Create, retrieve, and delete tasks
- Task properties: title, description, due date, priority (LOW / MEDIUM / HIGH), completion status
- Auto-generated IDs and database persistence

## Getting Started

### Prerequisites
- Java 17
- PostgreSQL 15
- Maven

### Database Setup
```sql
CREATE DATABASE taskflow;
CREATE USER taskflow_user WITH PASSWORD 'your_password';
GRANT ALL PRIVILEGES ON DATABASE taskflow TO taskflow_user;
GRANT ALL ON SCHEMA public TO taskflow_user;
```

### Configuration
Set the following environment variables or update `application.properties`:
DB_URL=jdbc:postgresql://localhost:5432/taskflow
DB_USERNAME=taskflow_user
DB_PASSWORD=your_password
### Run the App
```bash
./mvnw spring-boot:run
```
Server starts on `http://localhost:8080`

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/tasks` | Get all tasks |
| POST | `/api/tasks` | Create a new task |
| DELETE | `/api/tasks/{id}` | Delete a task by ID |

### Example Request
```bash
curl -X POST http://localhost:8080/api/tasks \
  -H "Content-Type: application/json" \
  -d '{"title":"My task","description":"Details here","priority":"HIGH","completed":false}'
```

### Example Response
```json
{
  "id": 1,
  "title": "My task",
  "description": "Details here",
  "priority": "HIGH",
  "dueDate": null,
  "completed": false
}
```

## Related
- [TaskFlow Frontend](https://github.com/shivamnarula04/taskflow-frontend)
