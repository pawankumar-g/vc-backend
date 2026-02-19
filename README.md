# Apna Video Call - Backend (Express.js)

A robust backend server for the video calling application built with Node.js, Express, Socket.IO, and MongoDB.

## 🚀 Features

- **User Authentication** - Secure login and registration
- **Meeting Management** - Track meeting history and codes
- **WebRTC Signaling** - Socket.IO for peer-to-peer connection setup
- **Real-time Communication** - Chat and user presence
- **Database Integration** - MongoDB for data persistence
- **CORS Support** - Cross-origin resource sharing

## 🛠️ Tech Stack

- **Backend**: Node.js, Express.js
- **Real-time**: Socket.IO
- **Database**: MongoDB with Mongoose
- **Authentication**: bcrypt for password hashing
- **HTTP Status**: http-status package

## 📁 Project Structure

```
backend/
├── src/
│   ├── app.js                 # Main application file
│   ├── controllers/
│   │   ├── socketManager.js   # Socket.IO connection management
│   │   └── user.controller.js # User authentication logic
│   ├── models/
│   │   ├── user.model.js      # User schema
│   │   └── meeting.model.js   # Meeting schema
│   └── routes/
│       └── users.routes.js    # User API routes
├── package.json               # Dependencies
└── README.md                  # This file
```

## 🚀 Getting Started

### Prerequisites

- Node.js 18+
- MongoDB (local or cloud)
- Git

### Installation

1. **Install dependencies**
   ```bash
   npm install
   ```

2. **Start MongoDB**
   Make sure MongoDB is running on `mongodb://127.0.0.1:27017/chatApp`

3. **Configure database connection**
   Update `src/app.js` if using different MongoDB URL:
   ```javascript
   const connectionDb = await mongoose.connect("mongodb://127.0.0.1:27017/chatApp");
   ```

4. **Start the server**
   ```bash
   npm start
   ```

5. **Server will run on**
   `http://localhost:8000`

## 🔧 Available Scripts

- `npm start` - Start the production server
- `node src/app.js` - Run directly with Node.js

## 🌐 API Endpoints

### Authentication
- `POST /api/v1/users/register` - User registration
  ```json
  {
    "name": "John Doe",
    "username": "johndoe",
    "password": "password123"
  }
  ```

- `POST /api/v1/users/login` - User login
  ```json
  {
    "username": "johndoe",
    "password": "password123"
  }
  ```

### Meeting History
- `GET /api/v1/users/get_all_activity?token=<user_token>` - Get user meeting history
- `POST /api/v1/users/add_to_activity` - Add meeting to history
  ```json
  {
    "token": "user_token",
    "meeting_code": "abc123"
  }
  ```

## 🔌 Socket.IO Events

### Client to Server
- `join-call` - Join a video call room
- `signal` - WebRTC signaling data
- `chat-message` - Send chat message

### Server to Client
- `user-joined` - New user joined the call
- `user-left` - User left the call
- `signal` - WebRTC signaling data
- `chat-message` - Receive chat message

## 🗄️ Database Schema

### User Model
```javascript
{
  name: String (required),
  username: String (required, unique),
  password: String (required, hashed),
  token: String
}
```

### Meeting Model
```javascript
{
  user_id: String,
  meetingCode: String (required),
  date: Date (default: Date.now)
}
```

## 🔒 Security Features

- **Password Hashing**: bcrypt for secure password storage
- **Token-based Auth**: Random tokens for session management
- **Input Validation**: Request validation and sanitization
- **CORS Configuration**: Controlled cross-origin access
- **Error Handling**: Comprehensive error responses

## 🌐 CORS Configuration

```javascript
app.use(cors({
  origin: "*", // Configure for production
  methods: ["GET", "POST"],
  allowedHeaders: ["*"],
  credentials: true
}));
```

## 🚀 Deployment

### Railway
1. Connect GitHub repository
2. Set environment variables
3. Deploy automatically

### Heroku
1. Create Heroku app
2. Set MongoDB connection string
3. Deploy via Git

### VPS/Dedicated Server
1. Install Node.js and MongoDB
2. Clone repository
3. Install dependencies
4. Configure environment
5. Use PM2 for process management

## 🔧 Environment Configuration

### Development
- Database: `mongodb://127.0.0.1:27017/chatApp`
- Port: 8000
- CORS: Open for development

### Production
- Database: MongoDB Atlas or dedicated server
- Port: Environment variable or 8000
- CORS: Configured for specific domains

## 📊 Monitoring

- **Logs**: Console logging for development
- **Health Check**: Basic server status
- **Error Tracking**: Comprehensive error logging

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 🔧 Troubleshooting

### Common Issues

1. **MongoDB Connection Error**
   - Ensure MongoDB is running
   - Check connection string
   - Verify database permissions

2. **Port Already in Use**
   - Kill existing process: `taskkill /PID <PID> /F`
   - Use different port
   - Check for other Node.js processes

3. **Socket.IO Connection Issues**
   - Check CORS configuration
   - Verify client URL
   - Check firewall settings

---

**Built with ❤️ using Node.js, Express, Socket.IO, and MongoDB**
