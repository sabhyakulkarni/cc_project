# Function Execution Engine using Docker

This project provides a simple server for submitting, storing, and executing code functions in isolated Docker containers. It supports Python and JavaScript.

---

## Features

- Submit function with metadata (language, timeout, etc.)
- Store and list all functions
- Execute Python and JS functions in Docker containers
- Enforce timeout execution
- Basic REST API using Express.js
- Postman support for testing

---

## Project Structure

```
cc_project/
├── server/
│   ├── docker/
│   │   ├── Dockerfile.python
│   │   ├── Dockerfile.js
│   │   ├── function.py
│   │   ├── function.js
│   ├── index.js
│   ├── routes/
│   ├── controllers/
│   ├── models/
├── .github/
│   └── workflows/
│       └── ci.yml
├── package.json
├── README.md
```

---

## Docker Setup

```bash
# Build Python function container
docker build -f server/docker/Dockerfile.python -t python-func .

# Build JS function container
docker build -f server/docker/Dockerfile.js -t js-func .

# Run a container (example)
docker run --rm python-func
```

---

## API Endpoints

| Method | Endpoint           | Description             |
| ------ | ------------------ | ----------------------- |
| POST   | `/submit-function` | Submit a function       |
| GET    | `/functions`       | List all functions      |
| GET    | `/functions/:id`   | Get a specific function |
| PUT    | `/functions/:id`   | Update a function       |
| DELETE | `/functions/:id`   | Delete a function       |

We are testing it using Postman.

---

## Sample JSON for Function Submission

```json
{
  "name": "My Python Func",
  "route": "/hello",
  "language": "python",
  "timeout": 5,
  "code": "def handler():\n    return 'Hello from Python!'"
}
```

---
