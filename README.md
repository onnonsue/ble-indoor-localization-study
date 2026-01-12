# Uncertainty-Aware Indoor Localization for Safety-Critical Evacuation Systems

## 🔥 Research Motivation

> **In safety-critical evacuation, inaccurate localization is more dangerous than delayed guidance.**

Conventional indoor localization research focuses on minimizing geometric error (e.g., RMSE).
However, in disaster scenarios such as fires, this assumption breaks down:

* Localization errors are **systematic and structural**, not random
* Environmental conditions change **dynamically and unpredictably**
* Overconfident but incorrect localization leads to **dangerous evacuation decisions**

This research redefines indoor localization as a **risk-aware decision-making problem under uncertainty**, where safety—not precision—is the primary objective.

---

## 🎯 Core Research Question

**How can evacuation systems make safe and timely decisions when precise indoor localization is fundamentally unreliable?**

---

## 🔑 Design Principles

This work is guided by four system-level objectives:

| Principle        | Description                                    |
| ---------------- | ---------------------------------------------- |
| **Safety**       | Minimize worst-case exposure to hazards        |
| **Speed**        | Enable fast, computationally feasible guidance |
| **Accuracy**     | Reliable decision-making under uncertainty     |
| **Connectivity** | AI-driven automation and system integration    |

**Primary research focus:**

* **Accuracy → Localization as a probabilistic and mathematical problem**
* **Connectivity → AI-based automation and adaptive system design**

---

## 📌 Problem Analysis

### 1. Manual Beacon Deployment Is Not Scalable

Current BLE-based systems require **manual beacon placement** tailored to each building.
Any structural change or environmental modification requires rebuilding the deployment map.

**Limitation:**

* High human labor cost
* Low adaptability to new or damaged environments

**Research Direction:**
Formulate beacon placement as an **optimization problem** and design an **AI-assisted deployment system** that recommends beacon locations based on building topology and safety constraints.

---

### 2. Fundamental Limits of BLE RSSI

BLE RSSI measurements:

* Are **one-dimensional scalar observations**
* Cannot distinguish vertical separation or obstruction-induced attenuation
* Reflect environmental interaction rather than Euclidean distance

This results in a **partially observable system**, where different physical states produce similar measurements.

[
z_t = h(x_t, e_t)
]

* (x_t): true user location
* (e_t): latent environmental factors

---

### 3. Non-Stationary Disaster Environments

Disaster conditions violate the stationarity assumptions of indoor localization:

* Beacons may fail or be destroyed
* Signal propagation changes due to fire, smoke, or collapse
* Prior maps may become invalid

Localization systems must therefore operate under **non-stationary and degraded conditions**.

---

## 💡 Core Concept: Decision-Critical Localization

### Redefining Accuracy

Instead of Euclidean error, localization accuracy is defined as:

[
\textbf{Decision Accuracy} = P(\text{Safe Decision} \mid b_t)
]

where (b_t = P(x_t)) is the belief over possible user locations.

The system prioritizes **safe decisions with quantified confidence**, not precise coordinates.

---

## 🧠 AI-Driven Contributions

### 1️⃣ AI-Based Beacon Placement Optimization

Beacon deployment is modeled as an information-theoretic optimization problem:

[
\min_{\mathcal{B}} ; \mathbb{E}[H(P(X \mid \mathcal{B}))] + \lambda R(\mathcal{B})
]

* (H(\cdot)): localization uncertainty (entropy)
* (\mathcal{B}): beacon configuration
* (R(\mathcal{B})): robustness and redundancy term

This enables **customized, safety-aware beacon layouts** without manual tuning.

---

### 2️⃣ Probabilistic Localization Under Partial Observability

* Region-based localization instead of point estimates
* Multi-hypothesis tracking
* Confidence-aware sensor fusion (BLE + IMU + optional vision)

The system maintains a **belief distribution** over possible user locations.

---

### 3️⃣ Adaptive Operation in Non-Stationary Environments

* Online detection of sensor and beacon failures
* Dynamic trust weighting of sensors
* Graceful degradation under partial observability

---

## 🚦 Risk-Aware Evacuation Planning

Evacuation guidance is generated in **belief space**, not physical space:

[
\pi^* = \arg\min_{\pi} \mathbb{E}[\text{Hazard Exposure} \mid b_t]
]

Routing decisions minimize **worst-case risk**, not shortest distance.

---

## 🧑‍🤝‍🧑 Human-Centered Safety Design

The system explicitly supports **trust calibration**:

* Communicates uncertainty transparently
* Avoids overconfident instructions
* Adapts instruction granularity as uncertainty increases

---

## 🏗️ System Architecture

```
[Multi-Modal Sensors]
  └─ BLE / WiFi / IMU
        ↓
[Uncertainty-Aware Fusion Engine]
  └─ Belief Distribution
  └─ Confidence Estimation
        ↓
[Risk-Aware Decision Core]
  └─ Worst-case Risk Evaluation
        ↓
[Adaptive Evacuation Guidance]
  └─ Safety-first Instructions
```

---

## 🔬 Research Phases

### Phase 1: Uncertainty Characterization

* Real-world BLE deployment
* Structural vs. transient error analysis
* RSSI reliability modeling

### Phase 2: Probabilistic Localization

* Bayesian / particle filtering
* Zone-based estimation
* Multi-hypothesis tracking

### Phase 3: Safety-Optimized Evacuation

* Belief-space routing
* Conservative fallback strategies
* User studies on uncertainty communication

---

## 📊 Expected Contributions

### Theoretical

* Formal framework for safety-critical localization
* Decision-oriented accuracy metrics
* Beacon placement as an uncertainty minimization problem

### Practical

* AI-assisted beacon deployment tool
* Simulation platform with configurable uncertainty
* Design guidelines for disaster-resilient indoor localization

---

## 🚧 Project Status

### ✅ Completed

* Real-world BLE deployment experiments
* Identification of structural localization failures
* System architecture design

### 🔄 In Progress

* Simulation environment (ROS/Gazebo)
* Probabilistic fusion framework
* Risk-aware routing prototype

### 📅 Planned

* AI-based beacon placement algorithm
* Real-time environmental adaptation
* Human-in-the-loop evaluation

---

## 🤝 Collaboration

This project welcomes collaboration in:

* Indoor localization
* Robotics and AI
* Safety-critical systems
* Human-centered evacuation design

📧 **Contact**: [onnonsue@gmail.com](mailto:onnonsue@gmail.com)
🐙 **GitHub Issues**: Technical discussion and contributions welcome

---

> *In emergency systems, safety does not come from certainty,
> but from decisions that respect uncertainty.*
