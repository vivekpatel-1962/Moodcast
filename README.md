# 🎶 Moodcast

Moodcast is a **full-stack music streaming platform** that empowers users to discover, share, and listen to music collaboratively. It features real-time music rooms, recommendations powered by ML, YouTube integration, and a sleek, responsive UI.

## ✨ Unique Features

- **Real-Time Music Rooms**: Create and join rooms with collaborative song queues, voting, and live chat powered by Socket.IO.
- **YouTube Integration**: Search, play, and manage YouTube tracks directly within the app.
- **Simulated Downloads**: Download playlists and songs for offline use (simulated for demo purposes).

## 🚀 Features

- Secure authentication via Clerk (supports email/password and social login).
- Homepage with personalized music recommendations.
- Room management: create, join, leave, and customize music rooms.
- Song queueing and voting in real time.
- Lyrics display
- Playlist and library management.
- Optional room chat for communication.
- Modern, responsive UI with TailwindCSS.

## 🛠️ Technologies Used

- **Frontend**: React, Vite, TailwindCSS, React Router, Socket.IO client, Clerk (auth)
- **Backend**: Node.js, Express, Socket.IO, sample/mock data, optional MongoDB
- **Integration**: YouTube Data API (proxy endpoint), Python ML for recommendations

## 📖 How to Use

1. **Clone the repository.**

<<<<<<< HEAD
2. **Set up Clerk authentication:**
   - Create a Clerk app at [https://dashboard.clerk.com](https://dashboard.clerk.com).
   - Copy your Publishable Key and add it to `client/.env.local`:
     ```
     VITE_CLERK_PUBLISHABLE_KEY=pk_...
     ```

3. **Set up MongoDB (optional, for persistent data):**
   - Install and start MongoDB locally, or use a cloud provider like MongoDB Atlas.
   - In `server/.env`, add your connection string:
     ```
     MONGO_URI=mongodb://localhost:27017/moodcast
     ```
   - If MongoDB is not configured, the app will use in-memory storage (data will reset each server restart).

4. **(Optional) Configure YouTube API Key in `server/.env`:**
   ```
   YOUTUBE_API_KEY=your_key
   ```

5. **Install dependencies:**
   ```
   npm install
   npm run install:all
   ```

6. **Start development servers:**
   ```
   npm run dev
   ```
   - Backend: `http://localhost:4000`
   - Frontend: `http://localhost:5173`

7. **Open the app:**  
   Go to [http://localhost:5173](http://localhost:5173) in your browser.

---


## 📚 API Endpoints

- `GET /api/recommendations` – Get music recommendations
- `GET /api/rooms` / `POST /api/rooms` – List/create rooms
- `POST /api/rooms/:id/join` – Join a room
- `POST /api/rooms/:id/queue` – Add song to queue
- `POST /api/rooms/:id/vote` – Vote on songs
- `GET /api/playlists` – Fetch playlists
- `GET /api/songs/:id/lyrics` – Get song lyrics
- `GET /api/yt/search?q=QUERY` – YouTube search

## 🤝 Contributing

Feel free to submit a pull request or open an issue for suggestions and improvements.

---

Happy listening & coding! 🎵🚀
=======
## Environment & YouTube Setup
1. Create a file `server/.env` and add:
```env
YOUTUBE_API_KEY=YOUR_YOUTUBE_DATA_API_V3_KEY
```
2. Restart the dev server after changing `.env`.

### Test the YouTube proxy
- With the server running on port 4000, try:
```bash
curl "http://localhost:4000/api/yt/search?q=lofi%20hip%20hop"
```
- Expected: JSON with an `items` array. If you get `500 {"error":"YOUTUBE_API_KEY not set on server"}`, set the env var. If you get `502 {"error":"YouTube request failed"}`, check the server console for detailed status/body (invalid key, quota, etc.).

### Troubleshooting
- 500 YOUTUBE_API_KEY not set: Ensure `.env` contains the key and the server restarted.
- 403/400 from YouTube: Key invalid or quota exceeded. Inspect server logs for `status` and `body` (improved logging is in place) and verify key/quotas in Google Cloud Console.
- Network/timeouts: Verify internet access and that port 4000 is reachable from the client (Vite proxy is configured in `client/vite.config.js`).

## Auth routes
- Sign in: `/sign-in`
- Sign up: `/sign-up`
- Protected routes: `/rooms`, `/rooms/:id`, `/player`, `/library`, `/settings`
>>>>>>> 001db00 (Update recommender training and README; remove old presentation)
