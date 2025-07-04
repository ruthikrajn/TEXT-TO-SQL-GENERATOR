# Text-to-SQL Generator

**Author:** Ruthik Raj Nataraja  

---

## 🔍 Project Overview

This project focuses on the automatic generation of SQL queries from natural language input using modern NLP techniques. The aim is to enable users—especially those without technical expertise—to interact with databases using simple natural language, removing the need to learn Structured Query Language (SQL).

Using the `facebook/bart-base` transformer model, we fine-tuned it on a curated dataset (`b-mc2/sql-create-context`) to generate SQL queries. This approach demonstrates how language models can bridge the gap between user-friendly language and structured database queries.

---

## 📁 Dataset

We used the `b-mc2/sql-create-context` dataset, which includes:
- Natural language questions
- Contextual information
- Corresponding SQL statements

The dataset mainly includes **SELECT** queries and helps train models to understand and generate SQL accurately based on context.

---

## ⚙️ Model & Methodology

- **Model Used**: `facebook/bart-base`
- **Framework**: HuggingFace Transformers
- **Training Setup**:
  - Tokenization using `AutoTokenizer`
  - Fine-tuned with `Seq2SeqTrainer`
  - Learning rate: `1e-5`
  - Batch size: `16`
  - Epochs: `10`
  - Data Collator: for sequence alignment

The BART model, being a denoising autoencoder, proved suitable for this Seq2Seq task due to its powerful encoder-decoder architecture.

---

## 📊 Results

- **ROUGE Score**: `0.8758` (avg)  
  Indicates high overlap between generated SQL and reference queries.
- **Accuracy**: `26.93%` (exact match)
- **Strengths**:
  - Performs well on straightforward SELECT queries.
- **Limitations**:
  - Struggles with complex queries involving JOINs, subqueries, and underrepresented patterns.

---

## 🧪 Evaluation

Evaluation was performed on a test dataset disjoint from training/validation sets. We used:
- **ROUGE** (for n-gram similarity)
- **Exact Match Accuracy** (for query-level correctness)

---

## 🚧 Limitations & Future Work

- Current model supports only SELECT queries.
- Future plans include:
  - Support for INSERT, UPDATE, DELETE queries
  - Handling JOINs, CTEs, and subqueries
  - Integration with live databases for query execution validation
  - Experimentation with larger models (e.g., Falcon, GPT variants)
  - Improved handling of ambiguous and complex language inputs

---

## 🧠 Key References

1. Zhong, Victor, et al. “Seq2SQL: Generating Structured Queries from Natural Language Using Reinforcement Learning.” [arXiv:1709.00103](https://arxiv.org/abs/1709.00103)
2. Guo, Jiaqi, et al. “Towards Complex Text-To-SQL in Cross-Domain Database with Intermediate Representation.” [arXiv:1905.08205](https://arxiv.org/abs/1905.08205v2)
3. Xu, Xiaojun, et al. “SQLNet: Generating Structured Queries from Natural Language Without Reinforcement Learning.” [arXiv:1711.04436](https://arxiv.org/abs/1711.04436)

---


## 💡 Conclusion

This project validates the effectiveness of using transformer-based NLP models for the task of Text-to-SQL generation. While the model performs well on simple queries, there is significant scope for enhancing its capability in complex SQL generation. Our approach lays a solid foundation for further development in this domain.

---
