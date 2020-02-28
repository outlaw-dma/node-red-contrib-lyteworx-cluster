<img src="./readme/logo.jpg" width="300">


# node-red-contrib-lyteworx-cluster

## Run Node-RED on all your CPU cores


## Description

The [Node-RED](https://nodered.org/) framework runs on [Node.js®](https://nodejs.org), which by default runs in a single process and which uses a single cpu core.  This node allows Node-RED to run flows on multiple cores.

Most computers, from the smartphone to the enterprise server, have multiple cores.  To take advantage of this, Node.js has a module (called the [cluster](https://nodejs.org/api/cluster.html#cluster_cluster) module) that allows a Node.js program to run on multiple cores.


## Getting Started

## Installing

`npm i node-red-contrib-lyteworx-cluster`


## Basic Concepts

### 


### Terminology

- **Cluster**: A set of processes running on a single computer instance that can talk to each other using [Inter-Process Communication (IPC)](https://en.wikipedia.org/wiki/Inter-process_communication)
- **Worker**: A single process in a cluster.
- **Master**: A single process that acts as the parent to all Worker processes.  A Master process can create and stop worker processes.
- **Bingo Worker**: A single worker process out of all of the worker processes spawned that can be used for single-process tasks.  For example, if Node-RED is watching a file, the user may only want to execute a flow once per event, and not have every worker process fire at once.
- **Broadcast**: Send a message to every worker in the cluster at the same time.
- **Round Robin**: [Cycle through workers](https://en.wikipedia.org/wiki/Round-robin_scheduling) one at a time, sending a message to the next worker in order.

### 

## Runtime Modes

1. **Enable Clustering** - The default mode, which enables clustering (running all flows on all processes)

2. **Send to Random Worker** - Takes a message from the input and sends it to a random worker process. 
3. **runOnBingo** - Only passes the message to the output **if the current worker is the bingo worker**.  Does not allow the message to continue to if the worker is not the bingo worker.
4. **Send to Bingo Process** - Takes a message from the input and sends it to the bingo worker.
5. **Broadcast** - Takes the message and sends it to all available workers.
6. **RoundRobin** - Passes the message to the next worker selected using a round-robin scheduling algorithm. 
