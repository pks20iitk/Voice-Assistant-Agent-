Voice Assistant Agent

A multi-modal, real-time Voice Assistant built using LiveKit, Google Real-Time API, MEM0, and N8N MCP.
The system supports audio, text, image, and dynamic actions, enabling natural conversations and automated workflows such as playing music on Spotify.

⭐ Overview

This project integrates multiple components to create a powerful, real-time, intelligent voice assistant:

Component	Role
LiveKit	Provides real-time communication infrastructure, session handling, audio streaming, and room management.
Google Real-Time API	Enables high-quality real-time speech recognition and speech synthesis.
MEM0	Handles smart conversational memory storage, retrieval, and updates using natural language.
N8N MCP Server	Executes external workflows via Model Context Protocol (MCP), such as interacting with Spotify to play songs.
🎯 Objective

The objective of this project is to create a fully multimodal voice assistant capable of:

Understanding speech in real time

Responding with synthesized speech

Maintaining conversational memory

Performing external actions via workflows (e.g., playing Spotify songs)

Supporting audio, text, image, and other modalities inside LiveKit Rooms

🧩 Key Components Explained
1. LiveKit

LiveKit provides the core real-time infrastructure:

Manages rooms and sessions

Streams audio/video bidirectionally

Enables low-latency interaction

Works as the UI front-end and communication layer

This allows users to interact with the assistant using voice, video, text, and shared images.

2. MEM0 – Smart Conversational Memory

MEM0 allows storing and retrieving memory in a natural and structured way:

Stores long-term conversational knowledge

Automatically updates memory using natural language

Supports embedding & vector-based retrieval

Helps the voice assistant maintain continuity across sessions

Example:

“Remember that my favorite genre is jazz.”
This is stored and can later be retrieved to personalize Spotify recommendations.

3. N8N MCP Server

We built an MCP (Model Context Protocol) Server inside N8N:

Enables external tool execution

Creates workflows that the assistant can trigger

Example workflow:
📌 Play a Spotify song using the Spotify API

The assistant can do tasks like:

“Play Coldplay – Yellow on Spotify.”

This request is processed and forwarded to N8N MCP Workflow.

4. Google Real-Time API

Used for:

Speech-to-Text (STT) (real-time transcription)

🏗️ Architecture Diagram (Simplified)

┌────────────┐     Audio/Video     ┌──────────────┐
│   User      │ <---------------->  │   LiveKit     │
└────────────┘                      └──────────────┘
                                           │
                                           ▼
                                ┌────────────────────┐
                                │   Voice Assistant   │
                                │  (LLM + Logic)      │
                                └────────────────────┘
                                 │        │         │
                      STT/TTS    │        │ Memory  │ MCP Tools
                                 ▼        ▼         ▼
                          ┌────────┐  ┌────────┐  ┌──────────┐
                          │Google  │  │ MEM0   │  │  N8N MCP  │
                          │RT API  │  │ Memory │  │ Workflows │
                          └────────┘  └────────┘  └──────────┘
🚀 Features
✔ Real-time voice conversation
✔ Multi-modal support (audio, text, image)
✔ Long-term personalized memory via MEM0
✔ Spotify integration through N8N MCP
✔ Room & session management via LiveKit
✔ Fast STT & TTS using Google Real-Time API


📦 Installation & Setup
1. Clone the repository

git clone https://github.com/pks20iitk/Voice-Assistant-Agent-.git
cd Voice-Assistant-Agent-
2. Create & activate virtual environment
python -m venv .venv
source .venv/bin/activate  # Linux / Mac
.\.venv\Scripts\activate   # Windows

3. Install dependencies
pip install -r requirements.txt

4. Set required environment variables

Create a .env file:

LIVEKIT_API_KEY=your_key
LIVEKIT_API_SECRET=your_secret
GOOGLE_API_KEY=your_google_api_key
MEM0_API_KEY=your_mem0_key
N8N_MCP_URL=http://localhost:5678/mcp
N8N_MCP_TOKEN=your_token

🎧 How It Works (Flow)

User speaks into the microphone

LiveKit streams audio

Google STT transcribes speech

LLM processes intent

MEM0 retrieves memory

If action needed → MCP workflow triggers (Spotify)

Assistant responds using Google TTS

LiveKit plays audio response back to the user

📝 Example Interaction

User: “Play my favorite jazz playlist.”
Assistant:

Retrieves memory → favorite genre = jazz

Triggers N8N workflow → Spotify → play playlist

Speaks back:
“Playing your jazz playlist on Spotify.”

📄 Future Enhancements

Add image understanding using Vision APIs

Support for personalized user profiles

Add WhatsApp / Telegram integration

More N8N workflows (emailing, calendars, IoT automation)

🤝 Contributing

Pull requests, improvements, and feature suggestions are welcome.

If you'd like, I can also:

✅ Generate a logo for the project
✅ Create a demo GIF section
✅ Write a Setup Guide, Architecture Docs, or API Reference

Just tell me!

Text-to-Speech (TTS) (natural & fast responses)

Provides low-latency results suitable for conversational AI.
