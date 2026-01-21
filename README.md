# Blockchain-Enhanced Network Scanning and Monitoring (BENSAM) Framework

The **Blockchain-Enhanced Network Scanning and Monitoring (BENSAM)** Framework is a conceptual, multi-layered system engineered for **comprehensive, verifiable, and tamper-proof network security**.  

By leveraging **blockchain technology**, modular design, and object-oriented principles, BENSAM provides a scalable and auditable approach to network monitoring and event verification.

---

## 🚀 Key Features

- **Modular Architecture** – Breaks down large, complex tasks into reusable and manageable subtasks.  
- **Object-Oriented Principles** – Applies the **Single-Responsibility Principle (SRP)** and **Dependency Inversion Principle (DIP)** for flexibility and loose coupling.  
- **Open-Closed Principle (OCP)** – Core logic interacts with abstract interfaces, making the system easily extensible without modification.  
- **Blockchain Integration** – Uses **Hyperledger Fabric** to ensure immutability, integrity verification, and auditable security events.  
- **Secure Data Flow** – Logs are hashed and stored off-chain with reference IDs recorded on-chain for verification.  
- **Automated Testing with pytest** – Simplifies test writing, encourages higher coverage, and ensures maintainability.  

---

## 🏛️ System Architecture

The BENSAM Framework follows a **multi-layered architecture**:

1. **Network Scanning Agents** – Generate raw security event logs.  
2. **Logging & Event Aggregator Layer** – Processes, filters, and hashes payloads.  
   - Stores full payload in an **Off-Chain Data Store**.  
   - Generates a transaction proposal containing the **hash, metadata, and reference ID**.  
3. **Blockchain Layer (Hyperledger Fabric)** –  
   - **Ordering Service** packages transactions.  
   - **Peer Nodes** endorse and commit transactions to the ledger.  
   - **Chaincode (Smart Contracts)** enforce compliance and policies.  
4. **Monitoring & Audit Layer** – Queries on-chain hashes, retrieves off-chain logs, recomputes hashes, and verifies integrity.

This ensures **tamper-proof, transparent, and auditable security monitoring**.

---

## 📂 Project Structure

```
Blockchain-Enhanced-Network-Scanning-and-Monitoring/
│── core.py          # Core logic orchestrating the pipeline
│── interfaces.py    # Abstract interfaces (Dependency Inversion Principle)
│── tests/
│    └── test_core.py  # Example pytest file with fixtures & parametrization
│── README.md        # Project documentation
```

---

## 🧩 Core Components

### `interfaces.py`
Defines **abstract interfaces** to decouple core logic from implementations.  
- Promotes **loose coupling** and **flexibility**.  
- Allows new modules to be added without modifying the core system.  

### `core.py`
Implements the **orchestration pipeline** using defined interfaces.  
- Follows the **Open-Closed Principle (OCP)**.  
- New data sources or processors can be added by implementing new classes.  

---

## ✅ Testing

The framework uses **pytest** for automated testing.  

### Why pytest?
- **Simple syntax** with plain `assert` statements.  
- **Fixtures** for reusable test setup/teardown.  
- **Parametrization** to run tests with multiple inputs.  
- **Rich plugin ecosystem** for flexibility.  

### Example Test File

```python
# File: tests/test_core.py
import pytest
from core import CoreLogic

@pytest.fixture
def sample_input():
    return {"event": "scan", "status": "success"}

@pytest.mark.parametrize("input_data", [
    {"event": "scan", "status": "success"},
    {"event": "monitor", "status": "failure"}
])
def test_core_processing(input_data):
    core = CoreLogic()
    result = core.process(input_data)
    assert "hash" in result
```

Run tests with:

```bash
pytest -v
```

---

## 🛠️ Installation & Usage

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/Blockchain-Enhanced-Network-Scanning-and-Monitoring.git
   cd Blockchain-Enhanced-Network-Scanning-and-Monitoring
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Run tests**
   ```bash
   pytest
   ```

---
Please cite this paper:  Hamdani, S. W. A., Ali, K., & Muhammad, Z. (2026). Blockchain-Enhanced Network Scanning and Monitoring (BENSAM) Framework. Blockchains, 4(1), 1. https://doi.org/10.3390/blockchains4010001
Research Paper: https://www.mdpi.com/2813-5288/4/1/1

## 📖 Future Directions

- Integration with real-world **network scanning tools**.  
- Extended blockchain support beyond Hyperledger (e.g., Ethereum, Polygon).  
- Advanced **AI/ML anomaly detection modules**.  
- Web-based dashboard for **visualizing audit logs**.  

---

## 📜 License

This project is licensed under the **MIT License** – feel free to use, modify, and distribute with attribution.
