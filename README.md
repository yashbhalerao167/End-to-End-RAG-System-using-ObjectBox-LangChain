
# End-to-End RAG Project using ObjectBox and LangChain

## Project Overview

This project implements an end-to-end Retrieval-Augmented Generation (RAG) system using LangChain and ObjectBox Vector Database. The goal of the application is to enable a Large Language Model (LLM) to answer user queries by retrieving relevant context from a collection of PDF documents.

The system processes PDF files, converts them into vector embeddings, stores them locally using ObjectBox, and uses a retrieval pipeline to provide accurate, context-aware responses. All data remains on-device, ensuring better privacy and lower latency.

The LLM used in this project is Groq’s LLaMA 3 (8B) model, integrated through LangChain.

---

## Architecture Overview

The RAG pipeline is implemented in the following stages:

### 1. Document Loading
PDF documents are loaded from a local directory using PyPdfDirectoryLoader from langchain_community. This allows batch ingestion of multiple PDF files.

### 2. Text Chunking
Loaded documents are split into manageable chunks using RecursiveCharacterTextSplitter.
- Chunk size: 1000 characters

### 3. Embedding Generation
Each text chunk is converted into a vector embedding using HuggingFaceBgeEmbeddings.

### 4. Vector Storage (ObjectBox)
The generated embeddings are stored in ObjectBox Vector Database, enabling fast and efficient similarity search while keeping all data local.

### 5. Language Model Setup
The LLM is configured using ChatGroq with the model:
- Llama3-8b-8192

### 6. Prompt Template
A ChatPromptTemplate is defined to structure how retrieved context and user queries are passed to the LLM.

### 7. Retrieval and Generation Chain
- A retriever fetches the most relevant document chunks from ObjectBox.
- A document chain combines the retrieved context with the prompt.
- A retrieval chain connects the retriever to the document chain to generate the final response.

---

## Installation and Setup

### Prerequisites
- Git
- Python 3.9+
- Basic command-line familiarity

### Step 1: Clone the Repository
```bash
git clone https://github.com/yashbhalerao167/End-to-End-RAG-System-using-ObjectBox-LangChain
```

### Step 2: Navigate to the Project Directory
```bash
cd End-to-End-RAG-Project-using-ObjectBox-and-LangChain
```

### Step 3: Create and Activate a Virtual Environment

Create the virtual environment:
```bash
python -m venv venv
```

Activate the virtual environment:

Linux / macOS:
```bash
source venv/bin/activate
```

Windows:
```bash
venv\Scripts\activate
```

### Step 4: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 5: Navigate to the App Directory
```bash
cd app
```

### Step 6: Run the Application
```bash
streamlit run app.py
```

### Step 7: Access the Application
Open the URL displayed in the terminal in your web browser.

### Step 8: Embed Documents
If required, click on the “Embed Documents” button in the application and wait until processing is complete.

### Step 9: Query the System
Enter questions related to the PDF files located in the us-census-data directory.
