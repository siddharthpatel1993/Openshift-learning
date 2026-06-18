<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/3/3a/OpenShift-LogoType.svg" alt="OpenShift" width="300"/>
</p>

<h1 align="center">☸️ OpenShift Learning Lab</h1>

<p align="center">
  <em>A hands-on collection of Kubernetes & OpenShift manifests for mastering container orchestration</em>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-OpenShift-EE0000?style=for-the-badge&logo=redhatopenshift&logoColor=white" alt="OpenShift"/>
  <img src="https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white" alt="Kubernetes"/>
  <img src="https://img.shields.io/badge/YAML-Manifests-CB171E?style=for-the-badge&logo=yaml&logoColor=white" alt="YAML"/>
  <img src="https://img.shields.io/badge/Status-Active_Learning-00C853?style=for-the-badge" alt="Status"/>
</p>

---

## 📋 Table of Contents

- [About](#-about-this-project)
- [Topics Covered](#-topics-covered)
- [Project Structure](#-project-structure)
- [Manifest Details](#-manifest-details)
- [Learning Progress](#-learning-progress)
- [How to Use](#-how-to-use)
- [Resources](#-resources)

---

## 📖 About This Project

This repository is a personal learning journey through **Red Hat OpenShift** and **Kubernetes**. It contains real-world YAML manifests covering deployments, services, routes, scaling, configuration management, and resource governance — built progressively from basic concepts to advanced patterns.

> 🎯 **Goal:** Prepare for OpenShift administration and build hands-on expertise with container orchestration concepts.

---

## 🎯 Topics Covered

| Category | Topics |
|----------|--------|
| **Workloads** | Deployments, ReplicaSets, Pod Management |
| **Networking** | Services (NodePort), OpenShift Routes |
| **Deployment Strategies** | Rolling Updates, Recreate Strategy |
| **Configuration** | ConfigMaps, Secrets, Volume Mounts |
| **Autoscaling** | Horizontal Pod Autoscaler (CPU & Memory) |
| **Resource Governance** | Resource Quotas, Limit Ranges, Requests & Limits |
| **Health Checks** | Readiness Probes, Liveness Probes |
| **Lifecycle** | PreStop Hooks, Graceful Shutdown |

---

## 📁 Project Structure

```
openshift-learning/
├── 📄 nginx-deployment.yaml              # Basic 3-replica Nginx deployment
├── 📄 nginx-service.yaml                 # NodePort service for Nginx
├── 📄 nginx-route.yaml                   # OpenShift Route for external access
├── 📄 recreate-deployment.yaml           # Recreate strategy with probes
├── 📄 rolling-update-deployment.yaml     # Rolling update with zero downtime
├── 📄 configmap-secret.yaml              # ConfigMap & Secret definitions
├── 📄 configmap-secret-deployment.yaml   # Deployment consuming config/secrets
├── 📄 hpa.yaml                           # HorizontalPodAutoscaler manifest
├── 📄 hpa-deployment.yaml                # Deployment for HPA testing
├── 📄 resource-limits-deployment.yaml    # Pod-level resource governance
├── 📄 resource-quota.yaml                # Namespace-level resource quota
├── 📄 limit-range.yaml                   # Container default limits
├── 📄 ipivrdeploy.yml                    # IPI/VR deployment manifest
├── 📄 openshift-kubernetes-training-book.pdf  # Training reference material
└── 📄 README.md                          # You are here!
```

---

## 🔧 Manifest Details

### 🟢 Basic Nginx Deployment
> `nginx-deployment.yaml`

A simple **3-replica** deployment using `bitnami/nginx`. The foundational building block for all other exercises.

---

### 🌐 Service & Route
> `nginx-service.yaml` · `nginx-route.yaml`

Exposes the Nginx deployment via a **NodePort** service and an OpenShift **Route** for external HTTP access.

---

### 🔄 Recreate Deployment
> `recreate-deployment.yaml`

Demonstrates the **Recreate** strategy — all old pods are terminated before new ones are created. Includes readiness probes and a full service/route stack.

---

### 🔁 Rolling Update Deployment
> `rolling-update-deployment.yaml`

Zero-downtime **rolling update** with `maxSurge=1`, `maxUnavailable=0`. Features readiness/liveness probes and graceful shutdown with `preStop` hooks.

---

### ⚙️ ConfigMaps & Secrets
> `configmap-secret.yaml` · `configmap-secret-deployment.yaml`

Injects configuration via **environment variables** and **volume mounts**. Demonstrates both ConfigMap and Secret consumption patterns.

---

### 📈 Horizontal Pod Autoscaler
> `hpa.yaml` · `hpa-deployment.yaml`

Auto-scales from **1 to 5 replicas** based on CPU (50%) and memory (70%) utilization thresholds.

---

### 🎛️ Resource Limits
> `resource-limits-deployment.yaml`

Deployment with explicit **CPU/memory requests and limits** demonstrating resource governance at the pod level.

---

### 🏗️ Quota & LimitRange
> `resource-quota.yaml` · `limit-range.yaml`

Namespace-level governance with:
- **ResourceQuota:** max 10 pods, 4 CPU, 4Gi memory
- **LimitRange:** container default limits and requests

---

## 📊 Learning Progress

| Topic | Status |
|-------|--------|
| Deployments | ✅ Complete |
| Services & Routes | ✅ Complete |
| Update Strategies | ✅ Complete |
| ConfigMaps & Secrets | ✅ Complete |
| Autoscaling (HPA) | ✅ Complete |
| Resource Management | ✅ Complete |
| Networking Policies | ⬜ Planned |
| RBAC & Security | ⬜ Planned |

---

## 🚀 How to Use

### Prerequisites

- Access to an **OpenShift cluster** with `oc` CLI installed, or a **Kubernetes cluster** with `kubectl`
- Basic understanding of YAML and container concepts

### Quick Start

```bash
# Login to your cluster
oc login --server=https://your-cluster:6443

# Create a project
oc new-project learning-lab

# Apply any manifest
oc apply -f nginx-deployment.yaml
oc apply -f nginx-service.yaml
oc apply -f nginx-route.yaml

# Watch pods come up
oc get pods -w

# Test autoscaling
oc apply -f hpa-deployment.yaml
oc apply -f hpa.yaml
```

### Verify Deployment

```bash
# Check deployment status
oc get deployments

# Get route URL
oc get routes

# Describe HPA status
oc describe hpa hpa-test-app
```

---

## 📚 Resources

- 📘 [OpenShift Documentation](https://docs.openshift.com/)
- 📗 [Kubernetes Official Docs](https://kubernetes.io/docs/)
- 📕 Training Book: `openshift-kubernetes-training-book.pdf` (included in repo)

---

<p align="center">
  <strong>🎓 Built with curiosity — OpenShift Learning Lab © 2026</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Made%20with-❤️-red?style=flat-square" alt="Made with love"/>
</p>
