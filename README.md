# IMS24173_DSC_212_ASSIGNMENT

MODULARITY ON THE KARATE CLUB GRAPH
DSC212 — GRAPH THEORY ASSIGNMENT

This repository presents a complete implementation of spectral modularity maximization on Zachary’s Karate Club graph, using Newman’s spectral approach for community detection.

The notebook includes:

* Modularity matrix construction
* Spectral bipartition using the leading eigenvector
* Recursive detection of multiple communities
* Graph visualizations at every split
* Computation of centrality measures
* Plots showing how metrics evolve during recursive splitting
* Interpretation and discussion of results

---

## REPOSITORY STRUCTURE

Karate-Modularity/
│── karate_modularity.ipynb — Main notebook executed sequentially
│── README.md — Project description and execution guide

---

## BACKGROUND

Zachary’s Karate Club is a classic social network of 34 individuals whose real-world division into two groups makes it a reliable test case for community detection algorithms.

Modularity evaluates how well a network is divided by comparing:

* Actual internal edges within communities
* Expected number of such edges in a randomized network with the same degree distribution

The modularity matrix is defined as:

**B = A − (k kᵀ) / (2m)**

The dominant eigenvector of **B** provides a meaningful split:

* Positive components → Community 1
* Negative components → Community 2

---

## ALGORITHM SUMMARY

### 1. Compute the Global Modularity Matrix

Based on adjacency information, node degrees, and total edges.

### 2. Spectral Bipartition

* Compute the largest eigenvalue and its eigenvector
* Divide nodes according to the sign of the eigenvector entries

### 3. Recursive Bisection

For every identified community:

* Form the restricted modularity matrix
* Compute its leading eigenvalue

Rules:

* If the leading eigenvalue is positive, the community can be meaningfully split
* If it is non-positive, the community is considered indivisible

The process continues until no community has a positive leading eigenvalue.

---

## VISUALIZATIONS

Each step of the recursion includes:

* Distinct colors assigned to different communities
* A fixed spring layout to maintain consistent node positions
* Node labels for readability
* A grid-like sequence showing the progression of splits

---

## CENTRALITY METRICS

After every split, the notebook computes:

* **Degree Centrality** — number of direct neighbors
* **Betweenness Centrality** — frequency of a node appearing on shortest paths
* **Closeness Centrality** — average distance to all other nodes
* **Clustering Coefficient** — tendency of a node’s neighbors to be interconnected

### Metric Evolution

Plots show how each node’s metrics vary through recursive partitioning, highlighting:

* Stable hub nodes
* Bridge nodes
* Core members of communities
* Changes in structural roles as the graph is split

---

## HOW TO RUN

1. Clone the repository
   `git clone <your-repo-url>`

2. Install the required packages
   `pip install numpy networkx matplotlib`

3. Open the notebook
   `jupyter notebook karate_modularity.ipynb`

4. Run all cells in order
   No manual adjustments are necessary.

---

## DISCUSSION (SUMMARY)

* The first spectral split aligns with the actual divide observed in the original Karate Club.
* High-degree and high-betweenness nodes serve as connectors between groups.
* Further recursive splitting uncovers smaller, naturally formed subcommunities.
* Metric evolution demonstrates how node roles shift as the network is partitioned.

---

## REFERENCE

Newman, M. E. J. (2006).
*Modularity and community structure in networks.*
Proceedings of the National Academy of Sciences, 103(23), 8577–8582.

---

## AUTHOR

Pranav S
Roll No: IMS24173
e notebook and run all cells from top to bottom. All required files will be generated automatically inside the figures/ folder.
