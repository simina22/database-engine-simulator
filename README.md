# Database Engine Simulator

This project is a lightweight simulation of a database engine implemented in Python.
It demonstrates core database concepts such as persistent storage, tree-based indexing,
and SQL-like query operations.

Originally developed as part of academic work, the project was later refined to present
a clean, professional demonstration of system design, data structures, and low-level
storage concepts.

---

## Features

- Persistent storage using a binary on-disk table
- Primary and secondary indexing with B-tree and B+ tree structures
- Support for range queries via linked B+ tree leaves
- SQL-like operations: insert, select, and delete
- Runnable Jupyter Notebook demonstrating system usage

---

## Implementation Overview (Python)

This project implements a simplified database engine with persistent storage and
multi-level indexing.

### Core components

- **Binary on-disk table (`products.dat`)**
  - Fixed-size records with stable byte offsets
  - Logical deletes implemented using a tombstone flag

- **Primary index**
  - B-tree on `product_id`
  - Used for fast point lookups on unique keys

- **Secondary indexes**
  - B+ tree on `price` (supports efficient range queries)
  - B+ tree on `category`
  - Leaf nodes are linked to allow sequential scans

- **Query interface**
  - SQL-like operations: `insert`, `select`, `delete`
  - Supports predicates such as:
    - `product_id = X`
    - `price BETWEEN low AND high`

### Data layout (high level)

Each product is stored as a fixed-size record in a binary file.
Indexes store **byte offsets** pointing directly to records on disk.

Deletes are implemented using a **tombstone flag**, preserving record offsets
while excluding deleted rows from query results.

---

## Technologies Used

- Python 3
- Jupyter Notebook
- File-based binary storage
- Custom implementations of B-tree and B+ tree data structures

---

## Project Structure

database-engine-simulator/
├── database-engine-demo.ipynb
├── README.md
├── .gitignore
---

## How to Run

1. Open `product_db.ipynb` in Jupyter Notebook
2. Run all cells in order
3. The notebook will create a local binary file (`products.dat`) for demonstration purposes
4. Sample insert, query, and delete operations will be executed automatically

---

## Notes

- The generated data file is intentionally excluded from version control
- This project focuses on backend and systems logic rather than UI
- Designed to illustrate how database engines combine on-disk storage with indexing
