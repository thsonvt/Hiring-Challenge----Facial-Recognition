# Hiring-Challenge----Facial-Recognition
Requirement Specifications for Facial Recognition and Authentication Prototype

EventNook is hiring for talented software engineers based in Vietnam to help them build the new products integrated into the core product. Engineers are invited to submit the solution to below challenge. There is a 2nd challenge at this link https://github.com/thsonvt/Hiring-Challenge---Website-Builder-with-AI-Chatbox-Integration/tree/main. You are welcome to attemp both challenges or you can just decide which challenge to take part. Cash award for the winner of each challenge is SGD 500

The CEO will be at the AI BuildCamp Demo Day on the morning of 22/02/2025 to talk about his company and the challenge in details. Interested candidates can speak to him at the event. Here is the event details https://lu.ma/x2a7cxn7




# 1. Project Overview
This project aims to develop a prototype for facial recognition and authentication that demonstrates:
Face Registration: Users can scan their faces through a weblink, which generates and stores a unique metadata token.
Check-In Verification: A secondary app scans the user again and verifies the live-scanned face against the stored token.
Security: Includes live detection to prevent spoofing (e.g., using photos or videos for authentication).
Accuracy: Adjustable accuracy parameters for matching.
The solution will leverage third-party cloud services, such as Amazon Rekognition API or Azure Face API, for facial recognition and matching, with a lightweight Node.js backend for token storage and interfacing with the web application.

# 2. System Requirements
## 2.1. Hardware Requirements
Devices with cameras (desktops, laptops, mobile devices).
Minimum resolution: 720p for clear face capture.

## 2.2. Software Requirements
Frontend: Responsive web application.
Backend: Node.js server with database integration.
Third-party APIs: Amazon Rekognition API or Azure Face API for facial recognition and matching.

# 3. Functional Requirements
## 3.1. Face Registration

### Weblink for Face Capture:
Users access a secure weblink to initiate face scanning.
The web app provides real-time feedback to guide face alignment within a frame.
The system uses liveness detection to ensure the face is scanned in real-time.

### Generate and Store Token:
The backend sends the captured face data to the selected third-party API (e.g., Amazon Rekognition, Azure Face API).
The API processes the face data and returns a unique metadata token (e.g., feature vector, faceId).
The backend securely stores the metadata token in a database along with user identifiers.

### Liveness Detection:
Verify the face is live by using the third-party API's liveness detection capabilities (e.g., depth detection, motion detection).
Reject static images, pre-recorded videos, or faces of sleeping individuals.
Save the data: The app will ask for basic personal info, such as name and email, and save it with a facial token.

## 3.2. Check-In Verification
### Real-Time Face Scanning:
The user scans their face through the check-in web app or another device.
The web app captures the face and submits it to the backend for processing.

### Token Matching:
The backend sends the scanned face data to the third-party API to generate a new metadata token.
The system matches the new token with the stored token.
The third-party API handles the comparison and returns a similarity score.

### Accuracy Parameters:
The backend provides an adjustable accuracy threshold (e.g., 70%-99%).
The match is successful if the similarity score meets or exceeds the threshold.

### Verification Outcome:
Success: The user is checked in and shows the name and email information that matches.
Failure: Prompt the user to retry or escalate for manual verification.

## 3.3. Security Features
### Live Detection:
Prevent spoofing using third-party API features like blink detection, motion prompts, and depth analysis.

### Data Encryption:
Encrypt stored tokens and transmitted data (e.g., AES-256 encryption).

### Fraud Prevention:
Log suspicious activities (e.g., repeated failed attempts, matching multiple users to the same token).

# 4. Non-Functional Requirements
### Performance:
Face capture, processing, and token generation should complete within 2 seconds.
Verification and matching should complete within 1 or 2 seconds.

### Scalability:
Support up to 1,000 concurrent users for scanning and verification.

# 5. Technical Specifications
## 5.1. Frontend
Technologies: HTML5, CSS3, JavaScript (React, Vue.js, or similar).
Camera Access: WebRTC or native device APIs.
UI Features:
Real-time face alignment feedback.
Progress indicators for capturing and processing.

## 5.2. Backend
Framework: Node.js with Express.js.
Token Management:
Securely store user metadata tokens in a database (e.g., Amazon DynamoDB).
Third-party API Integration:
Amazon Rekognition or Azure Face API for:
Face token generation.
Liveness detection.
Face matching.
API Endpoints:
/register: Capture and store face metadata.
/verify: Verify face against stored metadata.

## 5.3. Third-Party API Services
Amazon Rekognition API:
Use for face detection, token generation, and matching.
Built-in liveness detection and similarity scoring.
Azure Face API:
Face detection, recognition, and live verification.
Robust similarity and confidence score calculation.

## 5.4. Database
Type: Relational (PostgreSQL) or NoSQL (MongoDB).
Schema:
users table:
user_id: Unique identifier.
email: Email
name: Name
face_token: Encrypted metadata token.
created_at: Timestamp of registration.

# 6. User Flow

## Face Registration:
User opens a weblink and scans their face.
The app captures the face and sends data to the backend.
Backend interfaces with the third-party API, stores the metadata token, and confirms registration.
Check-In Verification:
User scans their face through a check-in web app.
Backend verifies the live scan against the stored token via the third-party API.
The system confirms success or prompts retry.

# 7. Testing and Validation
Accuracy Testing:
Validate token matching with various accuracy thresholds.
Liveness Detection Testing:
Test spoofing attempts using images, videos, and other methods.
Performance Testing:
Measure response time for token generation and matching.

# 8. Deliverables
Web app for face registration and verification.
Node.js backend for token storage and third-party API integration.
Integration with Amazon Rekognition or Azure Face API.
Documentation for setup, API endpoints, and usage.
