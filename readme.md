# SciNet: Evaluating AI Agents in Relation-Aware Scientific Literature Retrieval

![casefig](pics/casefig.png)

**SciNet** is the first comprehensive dataset designed to systematically evaluate the **relation-aware** retrieval capabilities of AI agents within large-scale scientific networks. While traditional retrieval paradigms rely on surface-level semantic matching, SciNetBench focuses on decoding the critical relational dynamics inherent in scientific discourse—such as identifying technological lineages, understanding peer assessments, and capturing the intrinsic disruption of research.

> Accepted by ICML 2026!

---

## 🔬 Benchmark Taxonomy

SciNetBench evaluates retrieval systems across three increasingly complex levels of relational abstraction:

### 1. Ego-centric Relation: Knowledge Structure Evaluation
* **Objective**: Assess publications based on intrinsic scientific properties derived from their structural position in the citation network.
* **Key Tasks**: Identifying the most **novel** (atypical knowledge combinations) or **disruptive** (paradigm-shifting) works within a research area.
* **Indicators**: Quantified via the Uzzi novelty Z-score and the Funk & Owen-Smith disruption index.

### 2. Pair-wise Relation: Peer Assessment & Context
* **Objective**: Identify specific relational contexts and fine-grained semantic associations between paper pairs.
* **Key Tasks**: 
    * **Citation Sentiment**: Distinguishing between supportive, critical, or neutral citations based on the citation context.
    * **Co-mention Retrieval**: Identifying papers jointly referenced within a coherent narrative segment, such as the same paragraph.

### 3. Path-wise Relation: Collective Dynamics
* **Objective**: Reconstruct the evolutionary trajectories of scientific ideas from foundational concepts to state-of-the-art methods.
* **Key Tasks**: Building a coherent citational and logical chain representing a scientific lineage (e.g., from *Neocognitron* to *Swin Transformer*).

---

## 📊 Dataset Specifications

* **Scale**: Built upon a massive meta-database of **269 million** scientific papers.
* **Domain Coverage**: Spans **7 major domains**: Artificial Intelligence, Biology, Medicine, Chemistry, Physics, Materials Science, and Geology.
* **Granularity**: Organized into **2,640 fine-grained subfields**.
* **Task Volume**: Comprises **8,940 curated tasks** validated through expert manual review.
* **Core Metadata**: Integrated from OpenAlex (July 2025 snapshot) and the full arXiv PDF corpus for high-fidelity text extraction.

---

## 📂 Repository Structure

### `Queries/`
Queries are organized by task category and scientific domain:

* **`Task1/` (Ego-centric)**:
    * `queries_task1_disruptive_[DOMAIN].json`: Queries for structural disruption.
    * `queries_task1_novel_[DOMAIN].json`: Queries for knowledge novelty.
* **`Task2/` (Pair-wise)**:
    * `queries_[DOMAIN]_pncites.json`: Sentiment-oriented citation tasks.
    * `queries_[DOMAIN]_cooccur.json`: Contextual co-mention tasks.
* **`Task3/` (Path-wise)**:
    * `queries_task3_path_[DOMAIN].json`: Evolutionary trajectory queries (e.g., `queries_task3_path_AI_KDD.json`).

### `Evaluation/`
Standardized evaluation scripts for all metrics:
* **Ego-Centric**: `task1-novelty-sos.py`, `task1-disruptive-recall.py`, `task1-novelty-llm.py`, etc.
* **Pair-Wise**: `task2-sentiment-cite-acc.py`, `task2-comention-acc.py`, etc.
* **Path-Wise**: `task3-path-connectivity.py`, `task3-path-llm.py`.

### `Subfields/`

The detailed lists of 2,640 fine-grained subfields across 7 scientific domains:

- `subfields_[DOMAIN].py`

---

## 🚀 Performance Insights

Our evaluation of 8 state-of-the-art retrieval methods reveals a significant performance gap:
* **Accuracy**: On relation-aware tasks, current retrieval accuracy often falls below **20%**.
* **Connectivity**: Even top-tier Deep Research agents struggle with maintaining explicit citational chains in path-wise reconstruction.
* **Alignment**: Current paradigms are largely misaligned with scientific practice, emphasizing the urgent need for relation-aware modeling.

---

## 📄 License
This project is licensed under the **MIT License**.