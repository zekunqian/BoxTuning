<div align="center">

# BoxTuning: Object-Aware Visual Prompting for Multimodal Model Fine-Tuning

[![NeurIPS 2026](https://img.shields.io/badge/NeurIPS-2026-b31b1b.svg)](https://openreview.net/)
[![Paper](https://img.shields.io/badge/Paper-OpenReview-blue)](https://openreview.net/)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

</div>

---

## 📢 News
* **[2026/09]** 🎉 **BoxTuning** has been accepted to **NeurIPS 2026**!
* **[Coming Soon]** 🚀 The official code is currently being organized and will be released soon. Stay tuned!

---

## 📖 Overview

Object-level spatial-temporal understanding is essential for video question answering, yet existing multimodal large language models (MLLMs) encode frames holistically and lack explicit mechanisms for fine-grained object grounding. While recent methods serialize bounding box coordinates as text tokens, this text-coordinate paradigm suffers from a fundamental **modality mismatch** and incurs a high token cost that forces aggressive temporal downsampling.

We propose **BoxTuning**, an object-aware visual prompting framework for MLLM fine-tuning that moves spatial-temporal object states from text-coordinate serialization into the visual stream while retaining only object identity in a compact text legend:
* **Colored Bounding Boxes & Trajectory Trails:** Directly rendered onto video frames to encode spatial geometry, inter-frame motion direction, and speed at full temporal resolution.
* **Compact Color-to-Object Legend:** Provides a minimal textual identity bridge (`~60–120` tokens) regardless of video frame count.

### ✨ Key Highlights
* **87–93% Text Token Reduction:** Compresses object descriptions from `611–1,241` tokens down to `61–120` tokens per sample across five video QA benchmarks.
* **1.52× End-to-End Speedup & Lower Memory:** Reduces overall inference latency by **34.0%** (including frame rendering overhead), cuts model FLOPs by **30.2%**, and lowers dynamic peak GPU memory by **37.8%**.
* **Consistent Accuracy Gains:** Surpasses text-coordinate baselines on spatially oriented benchmarks (**CLEVRER**, **Perception Test**, **STAR**) while avoiding context-budget degradation on reasoning-centric tasks (**NExT-QA**, **IntentQA**).

---

## 📊 Main Results

Comparison on five video QA benchmarks using the same VideoLLaMA2-7B backbone, upstream detector/tracker, and LoRA fine-tuning recipe:

| Method | CLEVRER | Perception Test | STAR | NExT-QA | IntentQA | Avg. Obj. Tokens | Latency (s/sample) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| VideoLLaMA2 (Base) | 67.9 | 66.0 | 66.5 | **79.8** | **76.7** | -- | -- |
| + ObjectMLLM (Text Coord.) | 77.6 | 66.6 | 67.2 | 78.5 | 75.5 | 1,000 | 0.5250 |
| **+ BoxTuning (Ours)** | **78.5** | **67.2** | **67.7** | 79.7 | 76.5 | **88 (-90.8%)** | **0.3465 (1.52×)** |

---

## 🗓️ Release Plan (TODO)

- [x] Paper accepted to NeurIPS 2026
- [ ] Release camera-ready paper
- [ ] Release official code (Coming soon)

---
