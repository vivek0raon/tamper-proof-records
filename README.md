# 🛡️ ChainOfCustody: Blockchain-Based Digital Evidence Management

> Immutable, Transparent, and Traceable Digital Evidence for Law Enforcement and Judiciary.

## 📄 Overview

Police and cybercrime units often struggle to maintain tamper-proof records of digital evidence (CCTV, mobile dumps, forensic reports). **ChainOfCustody** is a Web3-based platform designed to ensure the integrity of the "Chain of Custody" by recording every interaction with a piece of evidence on an immutable blockchain ledger.

## 🎯 Problem Statement

* **Tampering:** Risk of evidence manipulation or deletion in centralized databases.
* **Lack of Trust:** Disputes between defense and prosecution regarding evidence handling.
* **Fragmentation:** Disconnected systems between police stations, forensic labs, and courts.

## 💡 Solution Architecture

We utilize a **Permissioned Blockchain** (or Hybrid) to store the *metadata* and *cryptographic hashes* of evidence, while the heavy files are stored in a secure, encrypted off-chain storage (like IPFS or a secure cloud vault).

## 🛠️ Proposed Tech Stack

* **Blockchain:** Ethereum (Sepolia Testnet), Polygon, or Hyperledger Fabric (for enterprise permissioning).
* **Smart Contracts:** Solidity.
* **Backend:** Node.js / Express (for API handling).
* **Storage:** IPFS (InterPlanetary File System) for decentralized file storage + Pinata (for pinning).
* **Frontend:** React.js / Next.js + Tailwind CSS.
* **Web3 Integration:** Ethers.js / Web3.js.
* **Auth:** Metamask (Wallet) + JWT for role-based session management.

## 🚀 Project Roadmap & Phases

This project will be executed in **7 Strategic Phases**.

### Phase 1: Architecture & Design 🏗️

*Goal: Define data structures and user roles.*

- [ ] **Requirement Analysis:** Map out specific data points needed for evidence (Case ID, Officer ID, Time, Location).
- [ ] **Role Definition:** Define permissions for:
  - *Admin* (Superintendent)
  - *Investigator* (Upload/Transfer)
  - *Forensic Lab* (Analyze/Append)
  - *Judiciary* (Read-only/Verify)
- [ ] **System Architecture Diagram:** Design the flow between Client ↔ API ↔ Smart Contract ↔ IPFS.
- [ ] **UI/UX Wireframing:** Design dashboards for the Police and Court views.

### Phase 2: Smart Contract Development (The Core) ⛓️

*Goal: Create the immutable logic for the application.*

- [ ] **Setup Environment:** Initialize Hardhat or Truffle project.
- [ ] **Data Structs:** Create Solidity structs for `Evidence` and `ChainOfCustodyLog`.
- [ ] **Core Functions:**
  - `createEvidence()`: Mint a new record with hash.
  - `transferCustody()`: Change ownership from Officer A to Lab B.
  - `addAnalysisReport()`: Append forensic findings to the evidence chain.
- [ ] **Access Control:** Implement `onlyPolice`, `onlyCourt` modifiers.
- [ ] **Unit Testing:** Write Chai/Mocha tests to ensure contracts cannot be exploited.

### Phase 3: Secure Storage & Backend 🗄️

*Goal: Handle large files and encryption off-chain.*

- [ ] **IPFS Integration:** Set up scripts to upload files to IPFS and retrieve the CID (Content Identifier).
- [ ] **Hashing Algorithm:** Implement SHA-256 hashing of files *before* upload to verify integrity.
- [ ] **Backend API:** Create REST endpoints for the frontend to interact with (if a hybrid approach is used).
- [ ] **Encryption:** Ensure files are encrypted before IPFS upload so public IPFS nodes cannot view sensitive data.

### Phase 4: Frontend Development 💻

*Goal: Create an intuitive interface for non-technical users.*

- [ ] **Wallet Connection:** Integrate Metamask/WalletConnect for login.
- [ ] **Dashboard - Investigator:** Form to upload evidence details + Drag & Drop file zone.
- [ ] **Dashboard - Viewer:** A timeline view showing the history of the evidence (e.g., "Collected by Officer A at 10:00 -> Transferred to Lab at 14:00").
- [ ] **Verification Tool:** A public page where a judge can input a file hash to check if it matches the blockchain record.

### Phase 5: Integration & Events 🔌

*Goal: Connect the frontend to the blockchain.*

- [ ] **Web3 Wiring:** Use Ethers.js to call smart contract functions from the React UI.
- [ ] **Event Listeners:** Listen for blockchain events (e.g., `EvidenceTransfer`) to trigger real-time UI updates.
- [ ] **Audit Trail:** Build a visual log of all timestamps and actors associated with a Case ID.

### Phase 6: Security & Testing 🔒

*Goal: Ensure the system is bulletproof.*

- [ ] **Security Audit:** Check for re-entrancy attacks and permission loopholes in Smart Contracts.
- [ ] **Load Testing:** Simulate multiple officers uploading evidence simultaneously.
- [ ] **UAT (User Acceptance Testing):** Have a mock "Judge" try to verify tampered evidence (should fail).

### Phase 7: Deployment & Documentation 🚀

*Goal: Go live.*

- [ ] **Contract Deployment:** Deploy to a public testnet (Sepolia/Mumbai).
- [ ] **Frontend Hosting:** Vercel or Netlify.
- [ ] **Documentation:** Write a User Manual for officers on how to use the wallet and upload files.

## 📂 Folder Structure

```
/
├── contracts/          # Solidity Smart Contracts
├── backend/            # Node.js API & IPFS Logic
├── client/             # React/Next.js Frontend
├── scripts/            # Deployment scripts
├── test/               # Smart Contract Tests
└── README.md           # This file
```

## 🤝 Contributing

1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/NewFeature`).
3. Commit changes (`git commit -m 'Add NewFeature'`).
4. Push to branch (`git push origin feature/NewFeature`).
5. Open a Pull Request.
