# Realtime Code Collaborator

[![Live](https://synccode-34hb.onrender.com/)

A web application for real-time collaborative coding. Multiple users can join a “code room”, edit code live together, run code using an online API, and get AI-powered code reviews.

---

## 🎯 Features

- Real-time collaborative editing of code using **Monaco Editor**
- Join / leave rooms, list users in room
- Typing indicator (shows who is typing)
- Language selection (C++, JavaScript, Python, Java)
- Run/compile code with input support via [Piston API](https://github.com/engineer-man/piston)
- AI code review using Gemini (“Gemini-1.5-flash”) from Google Generative AI
- UI for copying room IDs, creating & joining rooms
- Modal view for displaying AI reviews (formatted with Markdown)

---

## 🧱 Tech Stack

| Layer | Technology |
|-------|------------|
| Backend | Node.js, Express, Socket.IO |
| Real-Time Communication | WebSockets (Socket.IO) |
| Code Execution | Piston API — remote code compile & run |
| AI Review | Google Generative AI (Gemini) |
| Frontend | React + React Hooks, Monaco Editor, React Markdown |
| Deployment | Static frontend served by backend; CORS enabled; runs on Render / similar |

---

## 🖐️ How It Works (High-Level)

1. Users open the frontend, enter a **room ID** and **user name**, then join a room or create a new one.  
2. Once in a room, the current code and language are synced, users see who else is present.  
3. As users type, their changes are broadcast to everyone in the same room.  
4. Changing language updates syntax / highlighting for all users.  
5. Users can run/compile code. The frontend sends the code & input to the backend, which uses Piston API to execute and returns output.  
6. Users can request an AI code review. The backend uses Gemini to generate a review, then broadcasts it.  
7. Rooms maintain current state (code + language) so new joiners see the latest.

---

## 🔧 Getting Started

### Prerequisites

- Node.js (≥14 or whatever your minimum is)  
- npm or yarn  
- Gemini API key (from Google Generative Models)  
- Internet connection (for Piston API and Gemini)  

### Setup

```bash
# Clone the repo
git clone https://github.com/sameergupta914/realtime-codecollaborator.git
cd realtime-codecollaborator

# Install dependencies for backend
cd backend
npm install

# Install dependencies for frontend
```

# Configuration

- Create a .env file in the backend folder with:

  GEMINI_API_KEY=your_gemini_api_key_here
  PORT=5001   # or your preferred port

realtime-codecollaborator/
├── backend/
│   ├── index.js (or server files)         # Socket.IO logic, Piston, Gemini integration
│   ├── .env                                # Gemini key, port
│   └── package.json, etc.
└── frontend/
    ├── src/
    │   ├── App.jsx                         # Main React component
    │   ├── components/ …                   # UI, editor, modals
    │   └── styles …
    ├── public/ …
    └── package.json

cd ../frontend
npm install
