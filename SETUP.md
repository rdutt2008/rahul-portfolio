# 🛠️ Setup Guide — Rahul Dutt's Portfolio Repository

This guide walks you through setting up the entire repository locally, including all dependencies for every project.

---

## ✅ Prerequisites

Before you begin, make sure you have the following installed:

| Tool | Version | Install Link |
|---|---|---|
| Python | 3.9+ | https://python.org/downloads |
| pip | latest | Comes with Python |
| Git | latest | https://git-scm.com |
| Node.js (optional) | 18+ | https://nodejs.org |

---

## 📥 Step 1 — Clone the Repository

```bash
git clone https://github.com/<your-username>/rahul-portfolio.git
cd rahul-portfolio
```

---

## 📦 Step 2 — Set Up a Python Virtual Environment

It's strongly recommended to use a virtual environment to keep dependencies isolated.

```bash
# Create the virtual environment
python -m venv venv

# Activate it
# On macOS/Linux:
source venv/bin/activate

# On Windows:
venv\Scripts\activate
```

---

## 📚 Step 3 — Install Shared Dependencies

```bash
pip install -r requirements.txt
```

The shared `requirements.txt` includes:

```
tensorflow>=2.12
numpy
pandas
matplotlib
scikit-learn
opencv-python
Pillow
```

---

## 🔑 Step 4 — Configure API Keys (AI Browser only)

The AI Collaborative Browser uses the **Gemini API**. You'll need a key from Google AI Studio.

1. Visit https://aistudio.google.com/app/apikey
2. Create a new API key
3. Create a `.env` file in `projects/ai-browser/`:

```bash
cd projects/ai-browser
cp .env.example .env
# Edit .env and paste your Gemini API key
```

`.env` format:
```
GEMINI_API_KEY=your_key_here
```

> ⚠️ Never commit your `.env` file. It's already in `.gitignore`.

---

## 🚀 Step 5 — Run Individual Projects

### 🌐 AI Collaborative Browser
```bash
cd projects/ai-browser
pip install -r requirements.txt
python main.py
```

### 🧬 DNA Sequence Detection
```bash
cd projects/dna-sequence-detection
python train.py           # Train the model
python predict.py         # Run predictions on sample sequences
```

### 🔬 Peptide Interaction Simulation
```bash
cd projects/peptide-simulation
python simulate.py        # Run thermodynamic simulation
# Output graphs saved to /output/
```

### 👁️ Diabetic Retinopathy Detection
```bash
cd projects/diabetic-retinopathy
# Download dataset from Kaggle first (see project README)
python preprocess.py      # Apply morphological transforms
python train.py           # Train CNN
python evaluate.py        # Check accuracy
```

### 🩺 Breast Cancer CNN
```bash
cd projects/breast-cancer-cnn
# Download dataset from Kaggle first (see project README)
python train.py
python evaluate.py
```

### 🖼️ Image Super Resolution (Django)
```bash
cd projects/image-super-resolution
pip install django
python manage.py migrate
python manage.py runserver
# Open http://127.0.0.1:8000 in your browser
```

---

## 🗂️ Step 6 — Project-Specific Data (Kaggle Datasets)

Several projects use Kaggle datasets. To download them:

1. Install the Kaggle CLI:
   ```bash
   pip install kaggle
   ```
2. Add your Kaggle API token to `~/.kaggle/kaggle.json`
3. Run the download script in each project:
   ```bash
   python download_data.py
   ```

---

## 🧪 Step 7 — Running Tests

```bash
# From the root of the repo
python -m pytest tests/ -v
```

---

## 🐛 Troubleshooting

| Issue | Fix |
|---|---|
| `ModuleNotFoundError` | Make sure your venv is activated and `pip install -r requirements.txt` was run |
| `GEMINI_API_KEY not found` | Check your `.env` file is in `projects/ai-browser/` |
| TensorFlow GPU errors | Run `pip install tensorflow-cpu` for CPU-only mode |
| Django `migrate` error | Make sure you're inside `projects/image-super-resolution/` |
| Kaggle download fails | Verify `~/.kaggle/kaggle.json` has valid credentials |

---

## 🤝 Contributing

See [.github/CONTRIBUTING.md](.github/CONTRIBUTING.md) for contribution guidelines.
