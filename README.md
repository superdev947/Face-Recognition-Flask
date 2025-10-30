# Face Recognition Web Application

A real-time face recognition web application built with Flask (backend) and React (frontend). This application uses your webcam to capture images and recognizes faces using the `face_recognition` library powered by dlib.

## 🎯 Features

- **Real-time Face Recognition**: Capture images from your webcam and identify known faces
- **Easy to Extend**: Simple structure to add multiple people for recognition
- **Modern Stack**: Flask REST API backend with React frontend
- **Cross-Origin Support**: CORS-enabled for seamless frontend-backend communication

## 🏗️ Project Structure

```
Face-Recognition-Flask/
├── flask-backend/          # Flask API server
│   ├── app.py             # Main Flask application
│   ├── face_rec.py        # Face recognition logic
│   ├── requirements.txt   # Python dependencies
│   ├── Procfile          # Deployment configuration
│   └── known-people/     # Directory for reference images
└── flask-frontend/        # React application
    ├── package.json       # Node dependencies
    ├── public/
    └── src/
        ├── App.js
        ├── components/
        │   └── webcam.js  # Webcam capture component
        └── ...
```

## 🚀 Getting Started

### Prerequisites

- Python 3.7+
- Node.js 14+
- npm or yarn
- Webcam access

### Backend Setup

1. **Navigate to the backend directory:**
   ```bash
   cd flask-backend
   ```

2. **Install Python dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Configure face recognition:**
   - Add reference images to the `known-people/` directory
   - Edit `face_rec.py` to add your known people:
     ```python
     # Replace 'your-name' with actual names and paths
     john = FaceRec('./known-people/john.jpeg', './stranger', 'John')
     jane = FaceRec('./known-people/jane.jpeg', './stranger', 'Jane')
     ```

4. **Update the API endpoint in `app.py`:**
   - Uncomment the code in `app.py`
   - Replace `your-name` with your actual person variable

5. **Run the Flask server:**
   ```bash
   python app.py
   ```
   The backend will run on `http://127.0.0.1:5000`

### Frontend Setup

1. **Navigate to the frontend directory:**
   ```bash
   cd flask-frontend
   ```

2. **Install Node dependencies:**
   ```bash
   npm install
   ```

3. **Start the React development server:**
   ```bash
   npm start
   ```
   The frontend will run on `http://localhost:3000`

## 📖 Usage

1. Open your browser and navigate to `http://localhost:3000`
2. Allow webcam access when prompted
3. Position your face in the webcam view
4. Click the "Click Me!" button to capture and recognize
5. The recognized name will appear below the button

## 🔧 Configuration

### Adding New People for Recognition

1. Add a clear photo of the person to `flask-backend/known-people/`
2. Update `face_rec.py`:
   ```python
   person_name = FaceRec('./known-people/person.jpeg', './stranger', 'PersonName')
   ```
3. Update `app.py` to use the new person object in the recognition logic

### Changing Backend URL

For deployment, update the API URL in `flask-frontend/src/components/webcam.js`:
```javascript
axios.post('YOUR_BACKEND_URL/api', {data : imageSrc})
```

## 📦 Dependencies

### Backend
- Flask 2.0.1 - Web framework
- face-recognition 1.3.0 - Face recognition library
- dlib 19.22.0 - Machine learning toolkit
- Flask-Cors 3.0.10 - Cross-origin resource sharing
- Pillow 8.3.1 - Image processing
- gunicorn 20.1.0 - WSGI HTTP server

### Frontend
- React 17.0.2 - UI framework
- react-webcam 5.2.4 - Webcam component
- axios 0.21.1 - HTTP client

## 🚢 Deployment

The project includes a `Procfile` for easy deployment to platforms like Heroku:

1. Create a Heroku app
2. Push your code to Heroku
3. Update the frontend API URL to your Heroku backend URL
4. Deploy the frontend to Netlify, Vercel, or your preferred hosting

## ⚠️ Important Notes

- The `app.py` file is currently commented out. You need to uncomment and configure it before running
- Replace all instances of `your-name` with actual identifiers
- Ensure good lighting for better face recognition accuracy
- The `stranger/` directory is created temporarily to process captured images

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 🐛 Troubleshooting

### Face Recognition Not Working
- Ensure good lighting conditions
- Position your face clearly in front of the camera
- Check if the reference image in `known-people/` is clear and properly named

### Backend Connection Issues
- Verify the Flask server is running on port 5000
- Check CORS configuration
- Ensure the frontend is pointing to the correct backend URL

### Installation Issues with dlib
- On Windows: Install Visual Studio Build Tools
- On Mac: Install cmake via Homebrew
- On Linux: Install build-essential and cmake
