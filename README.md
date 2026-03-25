# Project Aegis: Enterprise-Grade Private LLM Infrastructure
### A Study in Multi-Layered Security and Zero-Trust Network Topology

## Executive Summary
Project Aegis is a high-security, self-hosted Large Language Model (LLM) environment deployed on the **Microsoft Azure** cloud platform. The primary objective of this project was to architect a "Defense-in-Depth" infrastructure that allows for sophisticated AI interaction while maintaining a zero-exposure public profile. The resulting stack is accessible exclusively through an encrypted peer-to-peer (P2P) mesh network, ensuring absolute data sovereignty and protection against external adversarial actors.

---

## 🛡️ The Five-Layer Security Architecture (The Onion Model)
The system is engineered using a "Security Onion" approach, where five distinct defensive layers must be bypassed to reach the internal services.

### Layer 1: Cryptographic Authentication (SSH Hardening)
The external perimeter is secured via **Asymmetrical RSA-4096 Cryptography**. Password-based authentication has been programmatically disabled at the system level, rendering brute-force attacks computationally infeasible. Access is restricted to authorized holders of specific private keys.

### Layer 2: Network Perimeter Control (UFW)
A strict **"Default Deny" Firewall Policy** is enforced using the Uncomplicated Firewall (UFW). All public-facing ingress ports are cloaked. The system only permits traffic originating from the internal virtual network interface, effectively removing the server from global IP scanning databases.

### Layer 3: Reactive Intrusion Prevention (Fail2Ban)
The infrastructure employs **Fail2Ban** for automated threat mitigation. By monitoring system logs in real-time, the service identifies malicious probing attempts and triggers kernel-level IP bans after three failed authentication handshakes, neutralizing threats before they can escalate.

### Layer 4: Reverse Proxy Service Isolation (Nginx)
To prevent the exposure of internal application ports, **Nginx** is deployed as a Reverse Proxy. This layer abstracts the backend services (Ports 3000 and 11434), managing traffic flow and scrubbing HTTP headers. This ensures that the internal AI engines never interact directly with the network layer.

### Layer 5: Zero-Trust Mesh Encapsulation (Tailscale/WireGuard)
The core of the network topology is a **WireGuard-based encrypted tunnel**. The server is bound exclusively to a private mesh network. Without an authenticated, multi-factor-verified node on this VPN, the infrastructure remains invisible and unreachable from the public internet.

---

## ⚙️ Resource-Constrained Optimization & Engineering
This project served as a rigorous exercise in hardware efficiency and adaptive engineering:

* **Hardware Constraints:** Working within specific cloud subscription parameters, the deployment was limited in VRAM and CPU availability. I successfully performed a comparative analysis of model weights to select a **Quantized Dolphin-Phi Model**. This choice provided an optimal balance of reasoning capabilities and low-latency performance within restricted hardware bounds.
* **Network Topology Resolution:** A significant technical hurdle involved the orchestration of a Dockerized Web UI and a host-based inference engine. I successfully resolved complex "502 Bad Gateway" errors by re-architecting the internal bridge connections (`host.docker.internal`) and aligning the proxy-pass parameters with the encrypted VPN interface.

---

## 🧠 Strategic Implementation: Socratic Logic Engine
The LLM was not deployed as a standard assistant but was engineered with specific **System Logic Rules** to support university-level studies and personal technical development.
* **Objective:** To facilitate deep learning in university and college studies.
* **Logic Framework:** The model is programmatically constrained to act as a **Socratic Mentor**. It is instructed to avoid providing direct code solutions, instead identifying logical fallacies in the user's approach and utilizing guided inquiry to lead the user toward a self-derived solution.

---

## 🤖 Collaborative Development Disclosure
This infrastructure was developed through an iterative, high-level technical collaboration with **Gemini (Google AI)**. The AI served as a Senior Systems Architect, providing theoretical guidance on Linux networking, security hardening protocols, and infrastructure roadmap planning, while I executed the deployment, performed hardware benchmarking, and conducted real-time troubleshooting of the network stack.

---

## 🛠️ Technical Specifications
| Component | Technology |
| :--- | :--- |
| **Compute Environment** | Azure Ubuntu (LTS) |
| **Virtual Private Network** | Tailscale (WireGuard) |
| **Intrusion Prevention** | Fail2Ban |
| **Firewall Management** | UFW |
| **Web Gateway** | Nginx |
| **Orchestration** | Docker |
| **Inference Engine** | Ollama |
