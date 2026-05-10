<<<<<<< HEAD
# Expert Session Booking System

A full-stack application for booking 1:1 sessions with domain experts. Built with React, Node.js, Express, MongoDB, and Socket.io.

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 18, Vite, React Router v6 |
| Backend | Node.js, Express |
| Database | MongoDB, Mongoose |
| Real-Time | Socket.io |
| HTTP Client | Axios |

---

## Features

- **Expert Listing** — Search by name, filter by category, pagination, loading & error states
- **Expert Detail** — Full profile with time slots grouped by date
- **Real-Time Updates** — Slots instantly mark as booked across all connected clients via Socket.io
- **Booking** — Form with full validation, success confirmation, slot disabled after booking
- **My Bookings** — View all bookings by email with status (Pending / Confirmed / Completed)
- **Double-Booking Prevention** — Uses MongoDB queries to avoid duplicate bookings

---

## Project Structure

```
expert-booking/
├── backend/
│   ├── config/         # DB connection
│   ├── controllers/    # Business logic
│   ├── middleware/     # Error handler
│   ├── models/         # Mongoose schemas
│   ├── routes/         # Express routers
│   ├── seed.js         # Sample data
│   ├── server.js       # Entry point
│   └── .env.example
├── frontend/
│   └── src/
│       ├── components/ # Navbar, ExpertCard
│       ├── context/    # Socket context
│       ├── pages/      # ExpertList, ExpertDetail, BookingPage, MyBookings
│       └── utils/      # Axios config
└── README.md
```

---

## Setup & Installation

### Prerequisites
- Node.js 18+
- MongoDB running locally (or MongoDB Atlas URI)

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd expert-booking
```

### 2. Backend Setup

```bash
cd backend
cp .env.example .env
# Edit .env with your MongoDB URI
npm install
```

**.env file:**
```
PORT=5000
MONGO_URI=mongodb://localhost:27017/expert-booking
CLIENT_URL=http://localhost:5173
```

### 3. Seed the database

```bash
node seed.js
# Seeded 12 experts with time slots
```

### 4. Frontend Setup

```bash
cd ../frontend
npm install
```

### 5. Run both servers

**Terminal 1 (Backend):**
```bash
cd backend && npm run dev
# Server running on port 5000
```

**Terminal 2 (Frontend):**
```bash
cd frontend && npm run dev
# ➜ Local: http://localhost:5173
```

---

## API Reference

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/experts` | List experts (pagination + filter) |
| GET | `/experts/:id` | Expert details with slots |
| POST | `/bookings` | Create a booking |
| PATCH | `/bookings/:id/status` | Update booking status |
| GET | `/bookings?email=` | Get bookings by email |

### Query params for GET /experts
- `page` — page number (default: 1)
- `limit` — items per page (default: 6)
- `category` — filter by category
- `search` — search by name

---

## Features

### 1. Double Booking Prevention
Uses MongoDB's `findOneAndUpdate` with `$elemMatch` inside a **transaction** and `arrayFilters` to atomically check and mark a slot as booked. If two requests arrive simultaneously for the same slot, only one succeeds — the other gets a `409 Conflict` response.

### 2. Real-Time Slot Updates
Uses **Socket.io** rooms — clients join a room for the expert they're viewing (`expert_{id}`). When a booking is confirmed, the server emits a `slotBooked` event to that room. All connected clients instantly see the slot disabled without refreshing.

### 3. Input Validation
- Frontend: required fields, email regex, 10-digit phone check
- Backend: same validation + Mongoose schema validators
- Meaningful error messages returned for each failure

---

## Deployment (Optional)

**Backend:** Deploy to Render / Railway
- Set env vars: `MONGO_URI`, `CLIENT_URL`, `PORT`

**Frontend:** Deploy to Vercel / Netlify
- Set `VITE_API_URL` to your backend URL
- Set `VITE_SOCKET_URL` to your backend URL

**MongoDB:** Use MongoDB Atlas free tier

---

## Screenshots / Demo

> Record a short video showing:
> 1. Browsing and searching experts
> 2. Viewing available slots
> 3. Making a booking
> 4. Real-time slot update in another tab
> 5. Viewing My Bookings

---

## Author

Built as part of the Vedaz Software Development Internship assignment.
=======
# Expert-Booking-System
Expert booking platform with real-time slot updates, built using React, Express, Node.js and MongoDB.
>>>>>>> a41ff56667bb08802fc8ffb71edef71a1e430a0f
