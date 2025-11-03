# adv-week2
# 🧱 ADV Week 2 — Chilli: Vault + Escrow System on Solana

## 📦 Overview

**Chilli** is a decentralized **Vault and Escrow system** built on **Solana** using **Anchor** and **SPL Token**.  
It allows users to securely deposit SPL tokens into personal vaults and automatically release them to escrow when conditions (like target amounts or approvals) are met — ensuring **trustless, low-fee settlements**.

---

## 🚀 Problem

In traditional token transactions:
- Users pay **multiple transaction fees** — deposit, trade, transfer.
- In **peer-to-peer trades**, one side may **lose trust or funds**.

---

## 💡 Solution — The Chilli Program

Chilli combines:

🔹 **Vaults** — Securely accumulate SPL tokens until a goal is met.  
🔹 **Escrow** — Ensure fair, trustless token exchange.  
🔹 **Single Transaction Settlement** — Minimizes conversion and fee overhead.

---

## 👤 User Story — *Meet Alex*

> Alex often trades DRT tokens for SOL with other users.  
> Every trade costs him extra fees and trust risks.

Now with **Chilli**:
1. Alex deposits his DRT tokens into his Vault.  
2. Once the Vault reaches **1000 DRT**, it unlocks.  
3. Funds move to Escrow.  
4. Escrow releases tokens only when both parties approve.  
5. Resulting SOL is automatically sent to Alex’s wallet.

✅ Safe trade  
✅ Lower fees  
✅ Automated token handling  

---

## 🧩 System Flow
    ┌────────────────────────┐
    │        User Wallet     │
    │ (Holds DRT / SOL)      │
    └────────────┬───────────┘
                 │
                 ▼
    ┌────────────────────────┐
    │        Vault           │
    │  - Stores SPL Tokens   │
    │  - Tracks Target Amt   │
    │  - Releases on trigger │
    └────────────┬───────────┘
                 │
                 ▼
    ┌────────────────────────┐
    │        Escrow          │
    │  - Holds trade funds   │
    │  - Confirms parties    │
    │  - Executes swap       │
    └────────────┬───────────┘
                 │
                 ▼
    ┌────────────────────────┐
    │       Settlement       │
    │   - Converts DRT→SOL   │
    │   - Sends to wallet    │
    └────────────────────────┘



---
![Uploading Untitled-2025-10-29-1907.png…]()

## 🔁 Step-by-Step Workflow

### 1️⃣ Initialize Vault
Create a new vault and define:
- SPL Token Mint (e.g., DRT)
- Target Amount (e.g., 1000 DRT)


```bash




| Step           | Action              | Fee Paid       | Notes                   |
| -------------- | ------------------- | -------------- | ----------------------- |
| 1              | Deposit DRT → Vault | 1              | Locked                  |
| 2              | Vault Reaches 1000  | 0              | Unlocks                 |
| 3              | Move to Escrow      | 1              | Safe Lock               |
| 4              | Final Conversion    | 1              | Single Conversion       |
| **Total Fees** |                     | **2 tx only!** | Compare to 10+ normally |

ts-node scripts/createVault.ts
```
⚙️ Smart Contract Overview
🔸 Vault Logic

Stores SPL tokens in PDA

Allows deposits

Tracks progress and target

Releases tokens on condition

🔸 Escrow Logic

Holds tokens from both parties

Requires both approvals

Executes swap or returns funds

🔸 Security

PDAs prevent unauthorized access

Anchor #[account] enforces ownership
| Component     | Purpose                           |
| ------------- | --------------------------------- |
| **Vault**     | Secure accumulation of SPL tokens |
| **Escrow**    | Trustless trade between parties   |
| **SPL Token** | Standard for token transactions   |
| **Anchor**    | Smart contract framework          |
| **Solana**    | Fast, low-fee blockchain network  |


On-chain logs for full transparency
| Component      | Repository Link                                                         |
| -------------- | ----------------------------------------------------------------------- |
| 🪙 Token Vault | [👉 token_vault (click)](https://github.com/rahulpatle-sol/token_vault) |
