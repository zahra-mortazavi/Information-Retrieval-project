# 🏆 World Cup Match Search Engine

**A Professional Information Retrieval System for World Cup Matches (1930–2022)**

---

## 📖 Overview

This project implements a complete **Information Retrieval (IR) system** for searching and ranking football World Cup matches. The system processes structured and semi-structured match data, builds a **positional inverted index**, supports **fielded, boolean, and phrase queries**, and ranks results using **field-aware TF-IDF with a recency boost**.

> 🎯 Designed as a university project for the "Information Retrieval" course at the University of Isfahan.

---

## ✨ Features

- 🔍 **Rich Query Support** – simple keywords, fielded (`team:Argentina`), boolean (`AND`, `OR`, `NOT`), and phrase queries (`"Szymon Marciniak"`)
- 📄 **Document Construction** – each match becomes a rich document with separate fields (teams, players, captains, goals, xG, substitutions, etc.)
- 🧠 **Smart Preprocessing** – accent removal, lowercasing, stopword removal, plural‑to‑singular conversion, and handling of possessive `'s`
- ⚡ **Positional Inverted Index** – field‑aware and position‑aware for phrase searching and TF‑IDF scoring
- 📊 **TF‑IDF Ranking** – field‑weighted TF‑IDF with **dynamic recency boost** (newer matches get a slight advantage)
- ✅ **Evaluation Suite** – MAP, MRR, and Recall@k metrics over 10 curated queries (100% MAP and MRR achieved!)
- 🖥️ **Interactive Search** – run custom queries directly from the notebook

---

## 🗂️ Project Structure

```
├── src/
│   ├── data_preprocessing.py    # TextPreprocessor class
│   ├── document_builder.py      # DocumentBuilder class
│   ├── inverted_index.py        # InvertedIndex class
│   ├── query_processor.py       # QueryProcessor class
│   ├── tfidf_ranker.py          # TFIDFRanker class
│   └── evaluation.py            # Evaluation class + relevance builder
├── main.py                      # Main execution pipeline
├── matches_1930_2022.csv        # Dataset (964 matches)
└── README.md                    # This file
```

---

## 🚀 How to Run

1. **Clone or download** the project files.
2. **Install dependencies** (if needed):  
   ```bash
   pip install pandas numpy
   ```
3. Open the Jupyter Notebook (`ir.ipynb`) and run all cells – or run `main.py` directly:
   ```bash
   python main.py
   ```

4. The system will:
   - Load and clean the dataset
   - Build documents and the inverted index
   - Run sample queries
   - Perform evaluation and print MAP / MRR / Recall@100

5. To try your own queries, use the **interactive search cell** at the end of the notebook.

---

## 📊 Evaluation Results

| Metric | Value |
|--------|-------|
| **MAP** (Mean Average Precision) | **1.0000** |
| **MRR** (Mean Reciprocal Rank) | **1.0000** |
| **Overall Recall@100** | **0.9015** |

All 10 evaluation queries achieved perfect AP and RR scores, confirming high precision and correct ranking. Recall@100 is lower only for very broad queries (e.g., *yellow card* with 725 relevant documents), which is expected.

---

## 🛠️ Technologies Used

- **Python 3** – core logic
- **Pandas** – data loading and manipulation
- **NumPy** – numerical operations
- **Jupyter Notebook** – interactive development

*No external search libraries were used – everything is built from scratch.*

---

## 📌 Sample Queries You Can Try

```bash
messi
mbappe goal
team:Argentina round:Final
referee:"Szymon Marciniak"
messi AND mbappe
player:"Goncalo Ramos"
yellow cards argentina
0-0 draw
round:Semi-finals team:Morocco
```

## 📜 License

This project is for educational purposes only. Feel free to use and modify it for learning.

---

