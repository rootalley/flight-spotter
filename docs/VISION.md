# Product Vision: Flight Spotter

## 1. Introduction & Vision Statement

Flight Spotter is an augmented-reality (AR) mobile app for aviation enthusiasts that displays flight information just by pointing your camera at the plane. Unlike traditional flight tracking websites, our product offers a real-time, interactive "plane spotting" experience.

## 2. The Problem

Aviation enthusiasts and curious observers often see aircraft flying overhead (or taxiing on the ground) and wonder about their details—what airline is it, where is it going, what kind of plane is it? 

Existing solutions (like flight tracking websites) make users manually look up this information. This process is cumbersome and nearly impossible to do in the moment, causing the user to miss the opportunity to identify the plane as it passes. There is no seamless way to connect the physical sight of a plane with its digital information.

## 3. Target Audience

1. Enthusiasts and plane spotters who are passionate about aviation and want a tool to enhance their hobby.
2. Curious individuals and families who are interested in the planes travelling around them.
3. STEM educators and students who can use the app as a learning tool about aviation.

## 4. High-Level Goals & Key Features

Our primary goal is to create an engaging, real-time augmented reality experience for identifying aircraft.

*   **Goal 1: Instantly Identify Aircraft via Augmented Reality**
    *   **Feature:** Use the phone's camera, GPS, and orientation sensors to overlay flight data onto the live camera view. The app will "see" what the user sees and identify the planes in the frame.
    *   **Feature:** Allow users to tap on an identified plane in the AR view to see detailed information (e.g., flight number, airline, aircraft type, altitude, speed, origin, destination).

*   **Goal 2: Provide Rich, Real-Time Data**
    *   **Feature:** Integrate with one or more free, real-time Automatic Dependent Surveillance-Broadcast (ADS-B) data services to ingest aircraft transponder information.
    *   **Optional:** Display the selected aircraft's full flight path on a 2D map.

*   **Goal 3: Create an Engaging User Experience**
    *   **Feature:** A clean, intuitive interface that prioritizes the augmented reality view.

## 5. How It Works: A Functional Overview

At its core, the app's logic follows a simple, powerful sequence to create the AR experience:

1.  Use the phone's GPS to determine the user's location.
2.  Use the phone's orientation sensors (like the compass and gyroscope) to determine the direction the camera is pointing.
3.  Use the phone's lens/zoom settings to determine the camera's field of view.
4.  Request real-time data from an external ADS-B source for all aircraft currently flying within a reasonable radius of the user.
5.  Filter the flight data to determine which of those nearby aircraft should fall within the camera's current field of view.
6.  Capture a live video stream from the camera.
7.  Project an augmented-reality overlay on the camera stream to label identified aircraft.
8.  When a user taps an aircraft's label, the app displays a card with detailed information about that flight.
9.  (Optional) Display the selected aircraft's full flight path on a 2D map.

## 6. Architectural Principles & Open Questions

As we move toward implementation, here are a few key design decisions to be made:

*   **Abstract the Data Source:** Should we abstract the interface for the ADS-B data provider? This will allow us to switch between different data sources (e.g., from OpenSky Network to ADS-B Exchange) if necessary with minimal changes to the core application logic.

*   **AR Implementation Strategy:** There are two potential approaches for displaying AR labels. The simplest is to calculate the projected screen position of an aircraft based on its transponder data and the phone's sensors. A more complex alternative would involve real-time object recognition to visually identify planes in the camera feed. The optimal approach is an open question that will require prototyping and testing to evaluate performance and reliability.

*   **Flight Path Display:** Displaying the flight path on a 2D map may require historical transponder data, which might not be free of cost. We'd need to research if improvement in user experience is worth the cost and effort of implementation.

## 7. Technology & Stack (To Be Determined)

This section is a placeholder to document technology choices as they are made.

*   **Mobile Platform(s):** (e.g., iOS, Android, Cross-Platform)
*   **Frontend/AR:** (e.g., Swift/ARKit, Kotlin/ARCore, or a cross-platform solution like React Native or Flutter with an AR library)
*   **Backend:** (e.g., Firebase for user accounts/logbook, or a simple server to proxy data requests)
*   **Data Source:** (e.g., A public, free ADS-B data API like The OpenSky Network, adsb.lol, adsb.fi, airplanes.live, or ADS-B Exchange)
