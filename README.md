# LLMs for Automated ICD-10 Coding of Portuguese Obstetric Clinical Notes

This repository contains the experimental pipeline, evaluation code, and
analysis notebooks accompanying the paper:

**“Large Language Models for Automated ICD-10 Coding of Obstetric Clinical Notes in Portuguese”**

The study benchmarks multiple large language models (LLMs) for hierarchical
ICD-10 coding of Brazilian Portuguese obstetric discharge notes and compares
their performance against human inter-annotator agreement.

---

## 📌 Overview

Automatic ICD-10 coding from free-text clinical notes remains a challenging
problem, particularly in languages other than English.  
This work provides:

- A systematic benchmark of multiple general-purpose LLMs
- Evaluation at both three-character category and full (leaf-level) specificity
- Controlled Portuguese → English translation experiments
- Contextualization of model performance against blinded human validation
- Bootstrap-based uncertainty estimation (95% confidence intervals)

All experiments are conducted deterministically (temperature = 0) and follow
a fully reproducible, modular pipeline.

---

## 🧠 Models Evaluated

The benchmark includes the following models (accessed via API):

- GPT-4o  
- GPT-4o-mini  
- Sabiá-3.1  
- DeepSeek-V3  
- Gemini 1.5 Flash  
- Fine-tuned GPT-4o-mini (specialist variant)

Model outputs are constrained to structured JSON and validated using
ICD-10 normalization and regex-based filtering.

---

## 🔁 Experimental Pipeline

The workflow is organized into six sequential notebooks:

1. **LLM inference (Portuguese)**  
   Runs deterministic ICD-10 coding on Portuguese clinical notes.

2. **Portuguese → English translation**  
   Applies three translation strategies:
   - Google Translate
   - GPT-based translation
   - Sabiá-based translation

3. **LLM inference (English)**  
   Repeats ICD-10 coding using English-translated notes.

4. **Bootstrap confidence intervals (Portuguese)**  
   Computes 95% CIs for precision, recall, and F1-score via non-parametric
   bootstrap resampling (10,000 resamples, note-level).

5. **Bootstrap confidence intervals (English)**  
   Identical bootstrap analysis for translated notes.

6. **Aggregation and visualization**  
   Generates the final tables and figures reported in the paper and supplement.

Each notebook is self-documented and can be read independently.

---

## 📊 Evaluation and Statistics

- Task: multi-label ICD-10 assignment from full discharge notes
- Metrics: micro- and macro-averaged precision, recall, and F1-score
- Levels:
  - Three-character ICD-10 categories
  - Full leaf-level specificity
- Uncertainty: non-parametric bootstrap (95% CI)
- Human benchmark: blinded clinician validation on a stratified subset

---

## 🔐 Data Availability and Ethics

Clinical data used in this study are **not included** in this repository due to
privacy and ethical constraints.

The `data/README.md` file describes the expected data format and how the
experiments can be reproduced given appropriate institutional access.

No protected health information (PHI) is distributed.

---
