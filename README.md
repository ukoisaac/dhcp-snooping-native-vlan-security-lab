# 🔐 DHCP Snooping & Native VLAN Security Lab

## 📌 Overview

This lab demonstrates how to secure a Layer 2 network against **DHCP attacks** and **VLAN-based threats** using:

* DHCP Snooping
* Trusted vs Untrusted Ports
* Native VLAN Hardening

The topology simulates a **mini bank network**, including legitimate DHCP services and a rogue (attacker) server.

---

## 🎯 Objectives

* Configure **DHCP Snooping** on switches
* Define **trusted interfaces** for legitimate DHCP servers
* Block **rogue DHCP servers**
* Change and secure the **native VLAN**
* Understand real-world Layer 2 attack mitigation

---

## 🧱 Network Topology

<img width="1365" height="618" alt="DHCP SNOOPING (2)" src="https://github.com/user-attachments/assets/02fc8194-d3c7-4c03-958d-2b0248a7aa5c" />
<img width="1365" height="767" alt="DHCP SNOOPING" src="https://github.com/user-attachments/assets/1a7401a1-76cb-46a2-a354-372de33b5fa8" />




---

## ⚙️ Technologies Used

* Cisco Packet Tracer
* VLANs
* DHCP
* DHCP Snooping
* Native VLAN Configuration
* Cisco 2960 Switch
* Router (Inter-VLAN communication)

---

## 🔧 Key Configurations

### ✅ Enable DHCP Snooping

```id="2gkq0x"
ip dhcp snooping
ip dhcp snooping vlan 10,20,30
```

---

### ✅ Configure Trusted Port (Uplink to DHCP Server)

```id="v6k2gk"
interface fa0/3-4
ip dhcp snooping trust
```

---

### ❌ Untrusted Ports (Default Behavior)

* All access ports remain **untrusted**
* Rogue DHCP offers are automatically dropped

---

### ✅ Change Native VLAN (Security Best Practice)

```id="q0d1nb"
interface fa0/3-4
switchport mode trunk
switchport trunk native vlan 999
```

---

## 🧪 Test Scenarios

### 🔴 Rogue DHCP Server Attack

* A fake DHCP server was introduced into the network
* Switch identified it as **untrusted**
* DHCP offers were dropped → attack prevented

---

### 🟡 Legitimate DHCP Operation

* Trusted port allowed DHCP communication
* Clients successfully received valid IP addresses

---

## 🧠 Key Learnings

* DHCP Snooping prevents **man-in-the-middle attacks**
* Only trusted ports should allow DHCP server responses
* Native VLAN should be changed from default (VLAN 1)
* Layer 2 security is critical in enterprise environments

---

## 🚨 Real-World Use Case

In enterprise networks (e.g., banks), an attacker can plug in a rogue DHCP server to:

* Assign fake IP addresses
* Redirect traffic (MITM attack)
* Disrupt network access

This lab demonstrates how **DHCP Snooping blocks such attacks** and ensures only authorized DHCP servers operate.

---

## 📁 Lab File
FILE ATTACHED

``
## 👨‍💻 Author

**Isaac Uko**
Aspiring Network Engineer

---

## ⭐ Notes

This lab is part of my hands-on cybersecurity and networking practice focused on securing enterprise Layer 2 environments.

