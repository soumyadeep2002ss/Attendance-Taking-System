# Backend for Face Detection and Student Attendance System

This backend service, driven by FastAPI, is designed to enable real-time face detection and efficient management of student attendance records. Leveraging WebSocket for image data streaming, it provides endpoints for creating students and retrieving attendance data, making it an ideal solution for applications requiring facial recognition-based attendance tracking.

## Description

This backend server harnesses the capabilities of FastAPI, offering an asynchronous, high-performance framework for building APIs. Specifically crafted for systems reliant on live face detection, such as educational or security setups, it employs the `face-recognition` package to precisely identify and process faces within images or video streams.

### Face Detection with `face-recognition` Package

The face detection process involves the following steps:

1. **WebSocket Image Reception**: The `/ws` WebSocket endpoint accepts image data transmitted from clients. Upon connection, the backend receives image data in the form of bytes.

2. **Face Detection Logic**: Utilizing the `face-recognition` package, the backend's `handle_stream` function (located in `video_processing.face_detection`) performs face detection and recognition on the received image data.

3. **Processing and Recognition**: The `face-recognition` package analyzes the image data to identify faces, utilizing neural network-based models. Detected faces are recognized and processed, allowing for further actions such as attendance tracking or user identification.

## Setup and Usage

### Prerequisites

Ensure Python is installed on your system. This project requires the following dependencies:

- `fastapi`
- `opencv-python`
- `face-recognition`
- `dlib`

Install the dependencies by running:

```bash
pip install -r requirements.txt
```
### Running the Server

To start the backend server, execute the following command:

```bash
uvicorn app:app --reload
```
# Understanding Face Detection and Recognition with `face-recognition` Package

The `face-recognition` package is a powerful library used for precise face detection, recognition, and manipulation. Below is an overview of how this package functions:

## Face Detection

1. **Face Detection Algorithm**: The library employs a pre-trained deep learning model using a Histogram of Oriented Gradients (HOG) feature-based method with a linear classifier. This enables accurate detection of faces within images.

2. **Key Points and Features**: Detected faces are analyzed to identify specific facial features like eyes, nose, and mouth. These key points aid in understanding facial structure and distinguishing faces from backgrounds.

## Face Recognition

1. **Feature Extraction**: Once faces are detected, the package extracts numerical features representing unique patterns within each face, such as relative positions of facial components.

2. **Face Encoding**: These extracted features generate unique face "encodings" - compact numerical representations. These encodings facilitate easy comparison with other face encodings.

3. **Comparing Face Encodings**: For new faces, the library compares their encodings with previously stored encodings to determine similarity or distance, often using metrics like Euclidean distance.

## Usage in Applications

- **Face Verification**: It's utilized to verify if a face matches a known individual, common in biometric authentication systems.

- **Facial Recognition**: The library recognizes faces by comparing against a database of known faces, identifying or verifying individuals within a group.

## Customization and Adaptation

- **Transfer Learning**: The package allows fine-tuning or retraining of its face recognition model with additional data, enhancing accuracy or adapting to specific use cases.

- **Integration with Other Libraries**: It seamlessly integrates with OpenCV for image processing and can be combined with frameworks like TensorFlow or PyTorch for deeper customization and deployment.

The `face-recognition` package encapsulates these functionalities, offering a user-friendly interface for face-related tasks. It's widely used in security systems, attendance tracking, access control, and more.
