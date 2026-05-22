# Azure Honeynet SOC Lab (Microsoft Sentinel)

## Overview
In this project, I built a simple honeynet in Microsoft Azure to see what happens when a machine is exposed to the internet.

I created a Windows virtual machine, opened it up to incoming traffic, and used Microsoft Sentinel to monitor and analyze real attack activity (mainly RDP brute-force attempts).

---

## Tools & Technologies
- Microsoft Azure (VMs, Networking)
- Microsoft Sentinel
- Log Analytics Workspace
- Windows Event Logs
- KQL (Kusto Query Language)

---

## Architecture

<img width="1536" height="1024" alt="! Architecture Diagram ( imagesarchitecture png)" src="https://github.com/user-attachments/assets/8cfec2c0-fee3-47be-b8c3-a1974e5426d2" />



The setup includes:
- A Windows VM exposed to the internet
- Logs sent to Log Analytics
- Microsoft Sentinel for monitoring
- GeoIP mapping to visualize attacker locations

---

## What I Did

### 1. Set Up the Environment
- Created a resource group and virtual network in Azure
- Deployed a Windows VM with a public IP
- Opened RDP (port 3389) to allow inbound traffic named= "DANGER-ANYTRAFFIC"

<img width="1009" height="429" alt="image" src="https://github.com/user-attachments/assets/9f069144-26bc-443d-9d4c-0a10a9ec0171" />

<img width="1016" height="579" alt="image" src="https://github.com/user-attachments/assets/f65f24f6-0d90-441e-b770-a4dd5688ece7" />

<img width="1005" height="356" alt="image" src="https://github.com/user-attachments/assets/778a51a3-66a6-40c5-bae5-48a4a9c98bd4" />

---

### 2. Created the Honeynet
- Left the VM exposed on purpose (Disabled Firewall)
- Allowed anyone on the internet to attempt login
- This attracted real-world attack traffic

<img width="266" height="299" alt="image" src="https://github.com/user-attachments/assets/79c7cf5b-763f-45db-882d-1a87542e4d23" />

---

### 3. Collected Logs
- Connected the VM to Log Analytics
- Enabled Windows Security logs
- Focused (filtered) on failed login attempts (Event ID 4625)

<img width="1039" height="608" alt="Screenshot 2026-05-21 133248" src="https://github.com/user-attachments/assets/85c9f58a-3a8e-4d9e-a461-2b323e7bf982" />


---

### 4. Monitored Activity in Sentinel
- Connected Log Analytics to Microsoft Sentinel
- Wrote simple KQL queries to find:
  - Failed login attempts
  - Repeated login attempts from the same IP
- Identified clear brute-force behavior

<img width="1015" height="305" alt="image" src="https://github.com/user-attachments/assets/df1be393-ec78-404c-93ea-d4d506dd60e7" />

<img width="972" height="692" alt="Screenshot 2026-05-21 133355" src="https://github.com/user-attachments/assets/d55217ed-db99-4a1b-aada-f7a6c4f1edea" />

<img width="994" height="631" alt="Screenshot 2026-05-21 133518" src="https://github.com/user-attachments/assets/87fbe841-32db-4c44-8696-a5c83e97ca22" />

---

### 5. Visualized the Attacks
- Used GeoIP data to map attacker locations
- Built a workbook to show:
  - Where attacks were coming from
  - How often they were happening

<img width="1010" height="635" alt="Screenshot 2026-05-21 133607" src="https://github.com/user-attachments/assets/4f945c68-97bb-4cbc-a056-d4a143183070" />
<img width="982" height="648" alt="Screenshot 2026-05-21 133642" src="https://github.com/user-attachments/assets/f0a30ef7-4590-4a8e-a353-89548ec5e98c" />
<img width="1170" height="508" alt="Screenshot 2026-05-21 133827" src="https://github.com/user-attachments/assets/a5a058b1-7e4e-4116-baea-e8ed17cb0a64" />

---

## What I Found
- The VM started getting attacked About 2 hours after being exposed, and inceased as time goes on
- Most activity was repeated failed RDP logins
- Many attempts came from the same IPs (likely automated)


<img width="747" height="612" alt="image" src="https://github.com/user-attachments/assets/5748e4d8-c59e-4b8a-89a8-fbfd994e6177" />

---

## What I Learned
- Exposed systems get targeted very quickly
- Logs are critical for understanding what’s happening
- SIEM tools like Sentinel make it much easier to detect patterns
- Even simple setups can show real attack behavior

---

## 💡 Skills I Practiced
- Setting up a SIEM (Microsoft Sentinel)
- Analyzing logs using KQL
- Detecting brute-force attacks
- Working with Azure cloud services
- Visualizing security data

---

## 🎥 Project Walkthrough Video
https://youtu.be/C43Mw3vQxsk
