# YouTube Video Summarizer  

## Overview  
This project provides an application that extracts audio from YouTube videos, transcribes the speech, and generates a summarized text version. It integrates **Whisper-1** for speech-to-text transcription and **Meta-Llama-3.1-8B-8192** for summarization. The implementation is optimized for **long videos** by handling chunked audio processing.  

## Features  
* Extracts audio from YouTube videos
* Supports **long videos** (handles >30 minutes with chunking)
* Uses **Whisper-large-v3-turbo** for transcription
* Summarizes transcriptions using **Llama3-8B-8192** via Groq API
* Integrated with **Gradio** for an easy-to-use web interface  

## Installation  
1. **Clone the repository**  
   ```bash
   git clone https://github.com/veydantkatyal/yt-video-summarizer.git
   ```
2. **Install dependencies**  
   ```bash
   pip install -q requests torch bitsandbytes transformers accelerate gradio sentencepiece yt-dlp datasets[audio] pydub groq python-dotenv
   ```
3. **Set up API keys**  
   - Create a `.env` file and add: (recommended)  
     ```
     HF_TOKEN=your_huggingface_token
     GROQ_API_KEY=your_groq_api_key
     ```
   - Or set them directly in the code:  
     ```bash
     HF_TOKEN=your_huggingface_token
     GROQ_API_KEY=your_groq_api_key
     ```
## Usage
Open this in colab environment and run the cells, it will automatically lunch Gradio GUI in browser

## How It Works  
1️⃣ **Extracts audio** from the provided YouTube URL using `yt-dlp`.  
2️⃣ **Splits audio** into chunks (for long videos >10 minutes).  
3️⃣ **Transcribes each chunk** using `Whisper-large-v3-turbo`.  
4️⃣ **Summarizes** the full transcription using **Groq’s Llama3 model**.  
5️⃣ **Displays the summary** in a Gradio web interface.  

## Dependencies  
- `transformers` (for ASR and LLM models)  
- `yt-dlp` (for audio extraction)  
- `pydub` (for audio chunking)  
- `requests` (for API calls)  
- `gradio` (for UI)  

## Limitations  
- **Free Groq API tier** has a rate limit (longer videos may require paid access).  
- **LLM token limit** can restrict large transcriptions.  
- **Slow inference** on CPUs—**GPU recommended** for local execution.  

## Future Improvements  
* Optimize chunk merging for better summaries  
* Improve processing speed with GPU acceleration  
* Add multi-language support for summaries  
