# simon-app

Simon Says Memory Game

A browser-based version of the classic Simon Says memory game, built with Streamlit. Watch the growing sequence of colors, then repeat it back by clicking the buttons — how many rounds can you get through?

Features
Three difficulty levels (easy, medium, hard) that control how long the color sequence stays visible before it's your turn
Animated color reveal, one color at a time
Click-to-answer color buttons (no typing required)
Round tracking and a game-over screen showing the correct sequence
"Play Again" to restart instantly
Project structure
.
├── simon_says_app.py   # Main Streamlit app
├── requirements.txt    # Python dependencies
└── README.md
Run locally
Clone or download this project and open a terminal in the project folder.
(Recommended) Create a virtual environment:
bash
   python3 -m venv venv
   source venv/bin/activate      # On Windows: venv\Scripts\activate
Install dependencies:
bash
   pip install -r requirements.txt
Run the app:
bash
   streamlit run simon_says_app.py
Your browser should open automatically to http://localhost:8501. If not, open that URL manually.
Deploy to Streamlit Community Cloud (free)
Push this project to a public (or private) GitHub repository, keeping simon_says_app.py and requirements.txt at the repo root (or note their path).
Go to share.streamlit.io and sign in with GitHub.
Click "New app", select your repository and branch, and set the Main file path to simon_says_app.py.
Click Deploy. Streamlit Cloud will install requirements.txt automatically and give you a public URL.
Deploy elsewhere (Docker / any host)

Any platform that can run a Python web process will work. Example Dockerfile:

dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
EXPOSE 8501
CMD ["streamlit", "run", "simon_says_app.py", "--server.port=8501", "--server.address=0.0.0.0"]

Build and run:

bash
docker build -t simon-says .
docker run -p 8501:8501 simon-says
How to play
Choose a difficulty and click Start Game.
Watch the sequence of colors light up in order.
Once it's your turn, click the colors in the same order Simon showed you.
Get it right → the sequence grows by one color and the next round begins.
Get it wrong → the game ends and shows you the correct sequence, plus the round you reached.
Click Play Again to start over.
Notes
Difficulty changes how long the sequence pauses before you're allowed to answer (easy = more time, hard = less time) — the colors themselves always display for a fixed, readable pace.
Game state is kept in Streamlit's session_state, so it persists across reruns within a single browser session but resets if the page is reloaded or the server restarts.
