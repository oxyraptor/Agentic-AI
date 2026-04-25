# Agentic AI

A hands-on, day-by-day exploration of agentic AI systems built with Google Gemini, OpenAI-compatible APIs, LangChain, LangGraph, and more. The series culminates in a production-ready personal AI agent served via a Gradio web interface.

---

## 📁 Project Structure

| File | Description |
|---|---|
| `day1.ipynb` | **Environment Setup & First Call** – Verify API keys and make a first chat completion call to the Gemini API. |
| `day2.ipynb` | **Multi-Turn Conversations** – Use message history to have Gemini generate a hard IQ question and then answer it. |
| `day3.ipynb` | **Agentic Loop** – Build a multi-step agentic workflow where the model identifies and elaborates on a business opportunity for Agentic AI. |
| `day4.ipynb` | **Multi-LLM Competition & Judging** – Query multiple LLMs (Gemini, Groq/Llama, Ollama) with the same prompt, then use Gemini as a judge to rank the responses. |
| `day5.ipynb` | **Personal AI Agent with Tools** – Build a conversational AI assistant grounded in your own resume/LinkedIn PDF, with tool calling (capture user email, log unknown questions), served via Gradio. |
| `app.py` | **Production Gradio App** – The packaged version of the day 5 agent, ready to run as a standalone web app. |
| `requirements.txt` | All Python dependencies (auto-generated via `uv`). |
| `.env` | API key configuration (not committed – see setup below). |

---

## 🚀 Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/oxyraptor/Agentic-AI.git
cd Agentic-AI
```

### 2. Create a Virtual Environment

```bash
# Create the environment
python -m venv venv

# Activate – macOS/Linux
source venv/bin/activate

# Activate – Windows
venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure API Keys

Copy the example below into a `.env` file in the project root and fill in your keys:

```env
GOOGLE_API_KEY=your_google_api_key

# Optional – required for day 4 multi-LLM comparison
OPENAI_API_KEY=your_openai_api_key
ANTHROPIC_API_KEY=your_anthropic_api_key
DEEPSEEK_API_KEY=your_deepseek_api_key
GROQ_API_KEY=your_groq_api_key

# Required for app.py Pushover notifications
PUSHOVER_TOKEN=your_pushover_app_token
PUSHOVER_USER=your_pushover_user_key
```

> **Note:** A Google API key (`GOOGLE_API_KEY`) is the only key required to run notebooks day1–day3. Additional keys unlock the multi-LLM features in day4 and the notification features in `app.py`.

---

## 🤖 Running the Personal AI Agent (app.py)

The `app.py` script launches a Gradio chat interface that acts as a personal AI assistant grounded in your resume.

1. Place your LinkedIn profile PDF at `me/Profile.pdf` and your resume at `me/RESUME.pdf`.
2. Set `self.name = "Your Name"` in `app.py`.
3. Run the app:

```bash
python app.py
```

4. Open the local URL printed in the terminal (e.g. `http://127.0.0.1:7860`) to start chatting.

The agent will answer questions about your background and can:
- **Record interested visitors** – captures name, email, and conversation context via Pushover notification.
- **Log unknown questions** – records any question it couldn't answer so you can follow up.

---

## 🛠️ Notes

- Always activate your virtual environment before running any notebooks or scripts.
- To deactivate the virtual environment, run `deactivate`.
- Notebooks are designed to be run in order (day1 → day5), as each builds on concepts from the previous day.
