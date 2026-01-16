# Benchmarking Spatial Reasoning in Vision-Language Models

This project presents a diagnostic evaluation of **Vision-Language Models (VLMs)** on fundamental spatial reasoning tasks.  
Despite strong performance on high-level vision-language benchmarks, modern VLMs often struggle with **basic geometric reasoning**, such as left–right orientation, symmetry, and relative size perception.

This repository contains the code, benchmarks, and evaluation pipeline used to analyze these failure modes.

---

## Motivation

Recent Vision-Language Models (e.g., LLaVA, GPT-4o, Claude) achieve impressive results on tasks like VQA and image captioning. However, prior work suggests that these models may rely on **semantic shortcuts** rather than grounded spatial understanding.

This project investigates:
- Whether VLMs update spatial relationships consistently under simple image transformations
- Whether larger models exhibit better perceptual grounding
- How controlled synthetic benchmarks expose systematic reasoning failures

---

## Benchmarks

We design two complementary evaluation settings:

### 1 Symmetry & Left–Right Consistency (COCO)
- Images from the **COCO 2017 validation set**
- Each image is evaluated **before and after horizontal flipping**
- Tasks include:
  - Symmetry detection
  - Object list consistency
  - Left–right spatial reasoning
- Evaluated under **viewer-centric** and **ego-centric** prompt formulations

### 2 Controlled Size Perception (Synthetic)
- Procedurally generated images with two geometric objects
- Exact ground-truth annotations for:
  - Shape
  - Color
  - Relative size
- Removes real-world visual noise to isolate perceptual reasoning

---

## 🤖 Models Evaluated

- **LLaVA-1.5 (7B, 13B)**
- **GPT-4o**
- **Claude 3.5 Sonnet**

Models are evaluated using identical prompts and a consistent scoring protocol.

---

## 📊 Key Findings

- VLMs frequently fail to update left–right relationships under image flips
- Larger models do **not** consistently outperform smaller ones on spatial reasoning
- Many models default to biased or inconsistent answers despite controlled inputs
- GPT-4o performs strongly on synthetic size perception, while open-source models struggle

These results suggest that current training objectives insufficiently encode **explicit spatial geometry**.

---

## Metrics

- **Flip-consistency**: whether predictions logically update after image transformations
- **Accuracy** on spatial comparison tasks
- **Jaccard similarity** for object list stability

---

## 🛠️ Tech Stack

- Python
- PyTorch
- Vision-Language Models (VLMs)
- COCO Dataset
- Synthetic data generation

---

## Paper and Presentation

A detailed write-up of the methodology and results is available here:  
**[Project PDF](https://drive.google.com/file/d/1FLGDoPnuqrmCZ2-_yBixmCiWyB6ohdeY/view?usp=drive_link)**

**[Presentation Slides](https://docs.google.com/presentation/d/1KoPlPSMyhYifx7oSTnl6k3lHaYQoc4TArmJ3SlYsSbU/edit?usp=sharing)**

---

## Future Work

- Extending benchmarks to 3D or embodied environments
- Fine-tuning VLMs on diagnostic spatial tasks
- Probing CLIP embeddings for latent spatial information
- Evaluating agent-based prompting strategies for spatial grounding

---

## 👤 Authors

- **Salvador Robles Herrera**  
- **Eshan Balachandar**  

The University of Texas at Austin

---

## 📜 License

This project is for academic and research use.  
Please cite or reference appropriately if used in research.
