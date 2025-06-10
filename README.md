# 🩺 AI Doctor with Vision and Voice

**AI Doctor** is a powerful multi-modal virtual healthcare assistant that listens to your symptoms, analyzes medical images (like skin conditions), and provides empathetic spoken responses. Built for accessibility and ease of use, this tool leverages the latest in vision, voice, and language models to offer intelligent health insights through a simple browser interface.

---

## 🌟 TECHNICAL ARCHITECTURE
<img width="1088" alt="image" src="https://github.com/user-attachments/assets/5c14181c-a053-4430-a368-675b24535c27" />



## 🌟 Features

- 🎤 **Voice-Based Interaction** – Speak your symptoms or questions directly to the app.
- 🖼️ **Image Analysis** – Upload medical images for visual examination.
- 🧠 **AI-Powered Diagnosis** – Utilizes large vision-language models for contextual diagnosis.
- 🔊 **Spoken Recommendations** – Replies with natural, empathetic voice responses.
- 💻 **Simple Web Interface** – Built with Gradio for seamless interaction.

---

## ⚙️ How It Works

1. 🗣️ The user speaks their health query and uploads an image via the web interface.
2. 🎧 Audio is transcribed to text using OpenAI’s **Whisper** model via the **Groq API**.
3. 🧑‍⚕️ The transcription and image are analyzed by the **LLaMA 3.2 Vision** model with a medical system prompt.
4. 📝 The model generates a detailed diagnosis and recommendations.
5. 🔁 The text response is converted to speech using **ElevenLabs API**.
6. 🧾 The final output includes:
   - Transcribed query
   - Doctor’s written advice
   - An audio player with spoken response
<img width="1086" alt="image" src="https://github.com/user-attachments/assets/2ee84e73-bd66-43e5-821a-f5ac5b166790" />

---

## 🛠️ Tech Stack

| Component         | Technology                  |
|------------------|-----------------------------|
| Frontend         | Gradio                      |
| Speech-to-Text   | Whisper via Groq API        |
| Vision-Language  | LLaMA 3.2 Vision             |
| Text-to-Speech   | ElevenLabs API              |
| Language         | Python                      |

---

## 🔑 Prerequisites

Ensure the following before setup:

- ✅ Python 3.8+
- ✅ FFmpeg & PortAudio installed
- ✅ API keys for **Groq** and **ElevenLabs**

---

## 🚀 Setup Instructions

### 1️⃣ Add API Keys

Create a `.env` file in the root directory:

```env
GROQ_API_KEY="your_groq_api_key"
ELEVENLABS_API_KEY="your_elevenlabs_api_key"

```
Replace `"your_groq_api_key"` and `"your_elevenlabs_api_key"` with your actual keys. The application uses `python-dotenv` to load these variables automatically if you are using pipenv. If not, you might need to load them manually in the python scripts.

### 2. Installing FFmpeg and PortAudio

#### macOS

1. **Install Homebrew** (if not already installed):

   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

2. **Install FFmpeg and PortAudio:**

   ```bash
   brew install ffmpeg portaudio
   ```


#### Linux
For Debian-based distributions (e.g., Ubuntu):

1. **Update the package list**

```
sudo apt update
```

2. **Install FFmpeg and PortAudio:**
```
sudo apt install ffmpeg portaudio19-dev
```

#### Windows

##### Download FFmpeg:
1. Visit the official FFmpeg download page: [FFmpeg Downloads](https://ffmpeg.org/download.html)
2. Navigate to the Windows builds section and download the latest static build.

##### Extract and Set Up FFmpeg:
1. Extract the downloaded ZIP file to a folder (e.g., `C:\ffmpeg`).
2. Add the `bin` directory to your system's PATH:
   - Search for "Environment Variables" in the Start menu.
   - Click on "Edit the system environment variables."
   - In the System Properties window, click on "Environment Variables."
   - Under "System variables," select the "Path" variable and click "Edit."
   - Click "New" and add the path to the `bin` directory (e.g., `C:\ffmpeg\bin`).
   - Click "OK" to apply the changes.

##### Install PortAudio:
1. Download the PortAudio binaries from the official website: [PortAudio Downloads](http://www.portaudio.com/download.html)
2. Follow the installation instructions provided on the website.

### 3. Setting Up a Python Virtual Environment

#### Using Pipenv
1. **Install Pipenv (if not already installed):**  
```
pip install pipenv
```

2. **Install Dependencies with Pipenv:** 

```
pipenv install
```

3. **Activate the Virtual Environment:** 

```
pipenv shell
```

#### Using `pip` and `venv`
##### Create a Virtual Environment:
```
python -m venv venv
```

##### Activate the Virtual Environment:
**macOS/Linux:**
```
source venv/bin/activate
```

**Windows:**
```
venv\Scripts\activate
```

##### Install Dependencies:
```
pip install -r requirements.txt
```

#### Using Conda
##### Create a Conda Environment:
```
conda create --name myenv python=3.11
```

##### Activate the Conda Environment:
```
conda activate myenv
```

##### Install Dependencies:
```
pip install -r requirements.txt
```

## Running the application

The application is composed of several scripts that were developed in phases. The main application that provides the user interface is `gradio_app.py`.

To run the final application, execute the following command:
```
python gradio_app.py
```

This will start the Gradio web server, and you can access the AI Doctor interface in your browser, typically at `http://127.0.0.1:7860`.

### Development Phases

The project was built in several phases. If you want to test each component individually, you can run the scripts in the following order:

#### Phase 1: Brain of the doctor
This script contains the logic for analyzing the image.
```
python brain_of_the_doctor.py
```

#### Phase 2: Voice of the patient
This script handles recording audio and converting it to text.
```
python voice_of_the_patient.py
```

#### Phase 3: Voice of the doctor
This script handles converting text to speech.
```
python voice_of_the_doctor.py
``` 
