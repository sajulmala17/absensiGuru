# Teacher Attendance System

A modern web-based attendance system for teachers featuring face recognition and location-based attendance tracking.

## Features

- Face recognition for secure attendance verification
- Location-based attendance tracking
- Real-time attendance monitoring
- Check-in and check-out functionality
- Responsive design for all devices

## Prerequisites

Before you begin, ensure you have the following installed:
- Node.js (v18 or higher)
- npm (v9 or higher)
- A modern web browser with webcam support
- Internet connection (for geolocation and face recognition)

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd teacher-attendance-system
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

The application will be available at `http://localhost:5173`

## Configuration

### Face Recognition

The system uses TensorFlow.js and MediaPipe Face Detection for face recognition. The configuration is handled automatically, but you can adjust the detection sensitivity in `src/components/FaceRecognition.tsx`:

```typescript
const model = await faceDetection.createDetector(
  faceDetection.SupportedModels.MediaPipeFaceDetector,
  { 
    runtime: 'tfjs',
    // Add custom configuration here if needed
  }
);
```

### Location Services

The application uses the browser's Geolocation API and OpenStreetMap's Nominatim service for reverse geocoding. No additional configuration is required, but ensure:

1. Users grant location permissions when prompted
2. The device has GPS capabilities (for mobile devices)
3. Internet connection is available for address lookup

Location configuration can be found in `src/components/LocationPicker.tsx`.

## Usage

1. **Starting the Application**
   - Run `npm run dev` to start the development server
   - Open the provided URL in your browser

2. **Recording Attendance**
   - Click "Record Attendance" button
   - Allow camera access when prompted
   - Position your face in the camera frame
   - The system will automatically capture when a face is detected
   - Location will be recorded automatically

3. **Viewing Attendance Records**
   - All attendance records for the current day are displayed in the right panel
   - Records show check-in/check-out time and location

## Building for Production

To create a production build:

```bash
npm run build
```

The built files will be in the `dist` directory.

## Technical Details

### Dependencies

- React 18.3.1
- TensorFlow.js
- MediaPipe Face Detection
- React Webcam
- Lucide React (for icons)
- date-fns (for date formatting)
- Tailwind CSS (for styling)

### Project Structure

```
src/
├── components/
│   ├── FaceRecognition.tsx    # Face detection component
│   └── LocationPicker.tsx     # Location tracking component
├── types.ts                   # TypeScript interfaces
├── App.tsx                    # Main application component
└── main.tsx                   # Application entry point
```

### Browser Support

The application requires modern browser features:
- WebRTC (for camera access)
- Geolocation API
- WebGL (for face detection)

Supported browsers:
- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## Troubleshooting

1. **Camera not working**
   - Ensure camera permissions are granted
   - Check if another application is using the camera
   - Refresh the page

2. **Location not updating**
   - Enable location services on your device
   - Grant location permissions to the browser
   - Ensure you have an internet connection

3. **Face detection issues**
   - Ensure good lighting conditions
   - Position face clearly in the frame
   - Check if WebGL is enabled in your browser

## Security Considerations

- Face recognition is performed locally in the browser
- Location data is only collected when attendance is recorded
- No biometric data is stored permanently
- HTTPS is recommended for production deployment

## License

[MIT License](LICENSE)

## Support

For issues and feature requests, please create an issue in the repository.