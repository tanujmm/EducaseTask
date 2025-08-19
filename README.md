# School Management APIs

This project implements a simple School Management system using **Node.js**, **Express.js**, and **MySQL**.  
It provides APIs to:
- Add a new school
- List schools sorted by proximity to the user’s location

---

## ⚙️ Tech Stack
- Node.js
- Express.js
- MySQL (mysql2)
- dotenv (for environment variables)
- body-parser

---

## 🚀 Setup Instructions

### 1. Clone & Install
```bash
npm install
```

### 2. Database Setup
Run the SQL file provided in `schema.sql` to create the table:
```sql
CREATE TABLE schoolsT (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255) NOT NULL,
  address VARCHAR(500) NOT NULL,
  latitude FLOAT NOT NULL,
  longitude FLOAT NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 3. Environment Variables
Create a `.env` file in the root directory:
```env
PORT=3000
DB_HOST=localhost
DB_USER=root
DB_PASS=your_password
DB_NAME=schooldb
```

### 4. Start the Server
```bash
npm start
```

API will run on `http://localhost:3000`

---

## 📌 API Endpoints

### 1️⃣ Add School
**Endpoint:** `POST /addSchool`  
**Body (JSON):**
```json
{
  "name": "Greenwood High",
  "address": "123 Main St, City",
  "latitude": 12.9716,
  "longitude": 77.5946
}
```
**Response:**
```json
{
  "message": "School added successfully",
  "schoolId": 1
}
```

---

### 2️⃣ List Schools
**Endpoint:** `GET /listSchools?latitude=12.9716&longitude=77.5946`  

**Response:**
```json
[
  {
    "id": 1,
    "name": "Greenwood High",
    "address": "123 Main St, City",
    "latitude": 12.9716,
    "longitude": 77.5946,
    "created_at": "2025-08-20T12:00:00.000Z",
    "distance": 0
  }
]
```

Schools are sorted in ascending order of distance from the user’s coordinates.

---

## 📦 Deliverables
- `schema.sql` – Database schema
- `.env.example` – Environment variables template
- Postman Collection (`School Management.postman_collection.json`)
- Source code

---
