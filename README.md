# Smart AI Question Generator (Llama-3 Fine-Tuned)

An end-to-end Machine Learning system that generates intelligent questions (MCQs, True/False, Short Answer) from any PDF, Word document, or raw text. 

This project uses **Llama-3-8B** fine-tuned on a custom balanced QA dataset. It employs **RAG (Retrieval-Augmented Generation)** techniques to handle long documents and ensures diverse, non-repetitive question generation via "Smart Chunking."

## Key Features

- **Document Parsing:** Supports PDF (`.pdf`), Word (`.docx`), and plain text (`.txt`).
- **Fine-Tuned Llama-3:** Uses `unsloth/llama-3-8b-Instruct-bnb-4bit` as the base, fine-tuned with LoRA adapters for specific instruction following.
- **Smart Chunking (RAG-Lite):** Splits large documents into semantic chunks using LangChain to avoid hallucinations and context limits.
- **Customizable Generation:**
  - **Question Types:** Multiple Choice (MCQ), True/False, Short Answer, Long Answer.
  - **Difficulty Levels:** Easy, Medium, Hard.
  - **Control:** Choose the exact number of questions generated.
- **Interactive UI:** A user-friendly web interface built with **Gradio**.

## Tech Stack

- **Model:** Llama-3-8B (Unsloth, 4-bit Quantization)
- **Fine-Tuning:** PEFT (LoRA), Hugging Face Transformers, TRL
- **Orchestration:** LangChain (for text splitting/RAG)
- **Interface:** Gradio
- **Infrastructure:** Google Colab (T4 GPU supported)

## Project Structure

- `notebooks/`: Contains the Google Colab notebook for training and inference.
- `data/`: The balanced dataset used for fine-tuning.
- `model_adapter/`: The saved PEFT/LoRA adapter weights and tokenizer configurations.

## Installation & Usage

### Option 1: Run in Google Colab (Recommended)
Since this project uses a large Language Model (8B params), it requires a GPU. The easiest way to run it is via Google Colab.

1. Upload the `notebooks/QA Generator bot main.ipynb` file to Google Colab.
2. Upload the `data/final_balanced_QA_dataset.csv` to your Google Drive or Colab session.
3. Run the cells in order:
   - **Setup:** Installs dependencies (`unsloth`, `transformers`, `langchain`, etc.).
   - **Fine-Tuning:** Trains the model on the dataset (optional if using provided adapter).
   - **Inference:** Loads the model and launches the Gradio App.

### Option 2: Local Setup (Requires GPU)
If you have a powerful local GPU (NVIDIA RTX 3090/4090 or similar with 12GB+ VRAM):

1. Clone the repository:
   ```bash
   git clone [https://github.com/your-username/Smart-QA-Generator-Llama3.git](https://github.com/your-username/Smart-QA-Generator-Llama3.git)
   cd Smart-QA-Generator-Llama3
