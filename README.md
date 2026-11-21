# WiFi Billing & Hotspot Management System

![Status](https://img.shields.io/badge/Status-Production_Ready-success?style=for-the-badge)
![Integration](https://img.shields.io/badge/MikroTik-RouterOS_API_%26_RADIUS-blue?style=for-the-badge)
![Payments](https://img.shields.io/badge/Payments-M--Pesa_STK_Push-green?style=for-the-badge)
![Stack](https://img.shields.io/badge/Full--Stack-HTML_%7C_CSS_%7C_JS_%7C_PHP_%7C_Node_%7C_Python_%7C_SQL-orange?style=for-the-badge)

A **full-stack, production-ready WiFi Billing, Captive Portal, and ISP Hotspot Management System** engineered for seamless integration with **MikroTik routers**, **RouterOS API**, and **FreeRADIUS**. Built for ISPs, apartments, hostels, campuses, cyber cafés, and commercial hotspots, the platform automates user onboarding, package selection, **M-Pesa STK Push** payments, voucher generation, bandwidth control, and real-time revenue analytics—with zero manual intervention.

---

## ⚡ Key Highlights & Router Readiness

* **Plug-and-Play MikroTik & RouterOS Integration:** Connects directly to MikroTik routers via **RouterOS API** or **RADIUS** to provision hotspot users, bind MAC addresses, enforce upload/download speed profiles, and disconnect expired sessions automatically.
* **Zero-Touch M-Pesa STK Push Billing:** Users connect to WiFi, choose a time- or data-capped package on a fast captive portal, approve the M-Pesa prompt on their phone, and get online immediately upon payment callback.
* **Multi-Router & Multi-Zone Support:** Manage single hotspots or multiple remote MikroTik routers across different buildings and locations from one centralized admin dashboard.
* **Self-Service Session Recovery:** Paid subscribers can auto-reconnect or transfer access across devices using their M-Pesa transaction code or phone number.

---

## 🚀 Complete Feature Suite

### 1. Mobile-First Captive Portal (Client Side)
* **Instant Load Architecture:** Ultra-lightweight HTML5/CSS3/JS captive portal designed to open reliably on Android, iOS, Windows, and macOS devices immediately upon WiFi association.
* **Flexible Package Tiers:** Supports hourly, daily, weekly, monthly, unlimited, and data-volume packages (e.g., 1GB, 5GB, 10GB) with clear pricing and speed limits.
* **Live Payment Status Polling:** Real-time UI feedback while awaiting M-Pesa PIN confirmation, followed by automatic login redirect once payment succeeds.
* **Prepaid Voucher Redemption:** Built-in voucher login box for walk-in customers and resellers using printed access codes.

### 2. Full-Stack Billing Engine & Router Automation (Server Side)
* **Automated Provisioning:** Creates active hotspot users/profiles on MikroTik instantaneously when payment webhooks confirm successful transactions.
* **Bandwidth & Quota Enforcement:** Applies rate limits (e.g., `2M/5M`, `5M/10M`) and time/data caps directly at the router level.
* **Background Expiry & Cleanup Workers:** Automated cron jobs and daemon scripts continuously monitor active leases, revoke expired sessions, and keep router tables clean.
* **Transaction Reconciliation:** Verifies M-Pesa receipt numbers, amounts, and phone numbers server-side to prevent duplicate or spoofed activations.

### 3. Centralized ISP & Admin Control Panel
* **Live Network Telemetry:** View active connected users, current bandwidth usage, online/offline router status, and uptime in real time.
* **Package & Rate-Limit Manager:** Create, edit, enable, or disable WiFi plans and speed profiles without touching WinBox or router terminals.
* **Batch Voucher Generator:** Generate and export printable PDF/CSV voucher batches with custom prefixes, validity periods, and device limits.
* **Financial & Revenue Reporting:** Daily, weekly, and monthly M-Pesa collection summaries, transaction logs, and exportable accounting reports.

---

## 🛠️ Full-Stack Technologies & Languages Used

### Front-End (Captive Portal & Admin Dashboard)
* **HTML5:** Semantic captive portal templates, accessible forms, and structured admin views.
* **CSS3:** Responsive Flexbox & CSS Grid layouts, mobile-first breakpoints, custom design tokens, and dark/light admin themes.
* **JavaScript (ES6+) & TypeScript:** Asynchronous STK Push polling, voucher validation, live dashboard metrics, and REST API consumption.

### Back-End, Networking & Database Layer
* **PHP / Node.js / Python:** Full-stack server logic, Daraja/M-Pesa payment gateway APIs, webhook listeners, and automated expiry cron workers.
* **MikroTik RouterOS API & FreeRADIUS:** Direct socket/API communication with MikroTik routers for hotspot user creation, active session termination, and queue/profile management.
* **SQL (MySQL / PostgreSQL):** Relational database schema for routers, packages, hotspot users, vouchers, active sessions, and M-Pesa transaction ledgers.
* **REST APIs & Webhooks (JSON):** Secure communication between the captive portal, backend billing engine, payment providers, and network routers.

---

## 🏗️ System Architecture Flow

```text
[ User Connects to WiFi ]
          │
          ▼
[ MikroTik Captive Portal ] ──► Selects Package & Enters Phone Number
          │
          ▼
[ Full-Stack Billing API ] ───► Triggers M-Pesa STK Push
          │
          ▼
[ Payment Webhook Callback ] ─► Verifies Receipt & Logs SQL Transaction
          │
          ▼
[ MikroTik RouterOS API ] ────► Provisions User, Applies Speed Limit & Grants Internet
