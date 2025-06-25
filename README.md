# Sub 1 sat/vByte Bitcoin Node Directory

🚧 **Experimental Project**  
This is a **community-driven, experimental approach** to catalog Bitcoin nodes (economic and mining) that accept **sub 1 sat/vByte transactions**, including sub-dust or zero-fee transactions.  
It aims to support research, propagation, and testing of low-fee Bitcoin transactions across the network.

---

## 🧠 Purpose

Bitcoin Core nodes typically reject transactions below a `minrelaytxfee` threshold (default: 1 sat/vByte). This repo tracks nodes that intentionally **lower that threshold**, helping test and propagate transactions that would otherwise be dropped.

---

## 📥 How to Contribute

1. Fork the repo or submit a pull request.
2. Add your node info to the appropriate section.
3. Only submit if your node *actually accepts* sub-1 sat/vB transactions.

---

## 📄 Node Table Format


There are two categories:

- **Economic Nodes** – Full nodes used for wallets, payment relays, or research that *do not mine*.
- **Mining Nodes** – Nodes operated by mining pools or individual miners that *can include low-fee transactions in blocks*.

Each entry should include the following fields, see this example:

Name | Min Relay Fee (sat/vB) | Node IP / .onion | Public Explorer Available
|------------------------|------------------|---------------------------|---------------------------|
| `NodeName`           | `0.1`                  | `123.45.67.89:8333` or `abcxyz123.onion:8333` | Yes ([link](https://your-explorer.com)) / No |

---

## 🌍 Economic Nodes

Name | Min Relay Fee (sat/vB) | Node IP / .onion | Public Explorer Available
|------------------------|------------------|---------------------------|---------------------------|
| `David Coen's BTCpay Server`           | `0.1`                  | `zxycrhmh7lb3xsmlgd6464ou77mwsgi6wk2otap2rjlbr5kw3if5hsyd.onion:8333` | No |
| `sil3ntnod3`           | `0.1`                  | `f6rlgxnw2daki5mzvowdrqjaxh2mygrj5poijfpm7e6il63sbeiftaqd.onion:8333` | No |


_Add your node here if it's **not mining** but **accepts and relays** sub-1 sat/vByte transactions._

---

## ⛏️ Mining Nodes

Name | Min Relay Fee (sat/vB) | Node IP / .onion | Public Explorer Available
|------------------------|------------------|---------------------------|---------------------------|

_Add your node here if it's **a mining node** or relays transactions to mining infrastructure that accepts low-fee transactions._

---

## How to Set Up Your Node

If you want to support **sub‑sat/vbyte** transactions, follow these steps:

### 1. Lower the minimum relay fee

To relay transactions with fees below 1 sat/vbyte, you must lower your node’s minimum relay fee.

Edit your `bitcoin.conf` file, usually by running:

`bash
nano ~/.bitcoin/bitcoin.conf`

Then add or modify the following line:

`minrelaytxfee=0.00000100`

This sets the minimum relay fee to 0.00000100 BTC/kB, which equals 0.1 sat/vbyte — you can customize this parameter as you wish.

After saving the file (Ctrl+O, Enter, then Ctrl+X to exit), restart your node:

``bitcoin-cli stop``

``bitcoind``

### 2. Verify mempool policy

Once your node is running, check the active relay fee with:

``bitcoin-cli getmempoolinfo``

Ensure the minrelaytxfee field reflects your updated setting (e.g., 0.00000100).

## How to Connect to Sub-Sat Compatible Nodes

Your node will only relay and receive sub-sat/vbyte transactions if it connects to peers that also support them. 

To do this, you can choose a node from the list in this repository.

Connect manually using:

``bitcoin-cli addnode <ip>:<port> add``

Or add it permanently by updating your bitcoin.conf:

``addnode=<ip>:<port>``

    Confirm peer connections with:

``bitcoin-cli getpeerinfo``

Search the output for the target IP address to ensure a successful connection.

---

## 📌 Disclaimer

- Inclusion in this list does **not guarantee** that the node is online or reliable.
- Use this list for **testing, research, or propagation**, not production-critical transactions.
- Operators may update or remove their nodes at any time.

---

## 🔐 Security & Privacy Notice

- Use `.onion` addresses if you're privacy-conscious.
- Do **not expose** sensitive infrastructure without understanding the risks.
- Don't share nodes that don't belong to you unless you have permission.

---

## ✅ License

This project is open-source under the [MIT License](LICENSE).
