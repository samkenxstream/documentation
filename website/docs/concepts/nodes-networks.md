---
id: nodes-networks
title: Nodes and networks
sidebar_label: Nodes and networks
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';
import ClientStackPng from '@site/static/img/client-stack.png';
import NetworkPng from '@site/static/img/network.png';
import NetworkLayersPng from '@site/static/img/network-layers.png';


Ethereum is a decentralized **network** of computers running specialized software known as **Ethereum nodes** that communicate via peer-to-peer connections:

<img style={{width: 100 + '%', margin: 'auto', display: 'block', maxWidth: 461 + 'px'}} src={NetworkPng} /> 


## Nodes

An Ethereum **node** is a running instance of Ethereum's client software. This software is responsible for running the Ethereum blockchain. There are two primary types of nodes in Ethereum: **execution nodes** and **beacon nodes**. Colloquially, a "node" refers to an execution node and beacon node working together. This pair of nodes establishes connections with other pairs of nodes on other computers. This forms a network of nodes, each running the same software to process Ethereum blocks and transactions.

When users stake 32 ETH to participate in Ethereum's proof-of-stake consensus mechanism, they use a separate piece of software called a **validator client**, which connects to their Prysm beacon node. This is special software that manages validator keys and duties such as producing new blocks and voting on others' proposed blocks. An individual validator client depends on a beacon node, which depends on an execution node:

<br />

<img style={{width: 100 + '%', margin: 'auto', display: 'block', maxWidth: 651 + 'px'}} src={ClientStackPng} /> 

<br />

<table>
    <tr>
        <th style={{minWidth: 170 + 'px'}}>Component</th> 
        <th>Description</th>
    </tr>
    <tr>
      <td><strong>Ethereum node</strong><br />aka "Node"</td>
      <td>An Ethereum node is an <strong>execution node</strong> and <strong>beacon node</strong> working together. Ethereum nodes communicate peer-to-peer to secure the Ethereum network, and require both <strong>execution-layer client software</strong> and <strong>consensus-layer client software</strong>.</td>
    </tr> 
    <tr>
      <td><strong>Execution node</strong></td>
      <td>Execution nodes use execution client software to process transactions and smart contracts in Ethereum's <strong>execution layer</strong>. Nethermind, Besu, and Go Ethereum (Geth) are examples of execution client software.<br /> <br />An execution node will talk to other execution nodes via peer-to-peer networking, and to a local beacon node.</td>
    </tr>
    <tr>
      <td><strong>Beacon node</strong></td>
      <td>Beacon nodes use beacon node client software to coordinate Ethereum's proof-of-stake consensus. Prysm, Teku, Lighthouse, and Nimbus are consensus clients that contain both beacon node and validator client software. <br /> <br />A beacon node will talk to other beacon nodes via peer-to-peer networking, to a local execution node, and (optionally) to a local validator.</td>
    </tr>
    <tr>
      <td><strong>Validator</strong></td>
      <td>Validator clients are specialized software that let people stake 32 ETH as collateral within Ethereum's <strong>consensus layer</strong>. Validators are responsible for proposing blocks within Ethereum's proof-of-stake consensus mechanism, and will fully replace proof-of-stake miners after <a href='https://ethereum.org/en/upgrades/merge/'>The Merge</a>. <br /> <br />A validator will talk only to a local beacon node. A validator's beacon node tells the validator what work to do, and broadcasts the validator's work to the Ethereum network as the validator performs its duties.</td>
    </tr>
</table>


## Networks

The Ethereum network that hosts real-world applications is referred to as **Ethereum Mainnet**. Ethereum Mainnet is the live, **production** instance of Ethereum that mints and manages real Ethereum (ETH) and holds **real** monetary value.

There are other live, **test** instances of Ethereum that mint and manage **test** Ethereum. Each test network is compatible with (and only with) its own type of test ETH. These test networks let developers, node runners, and validators test new functionality before using real ETH on Mainnet.

Every Ethereum network is divided into two layers: **execution layer** (EL) and **consensus layer** (CL):

<img style={{width: 100 + '%', margin: 'auto', display: 'block', maxWidth: 323 + 'px'}} src={NetworkLayersPng} /> 

<br />

Every Ethereum node contains software for both layers: **execution-layer** client software (like Nethermind, Besu, Geth, and Erigon), and **consensus-layer** client software (like Prysm, Teku, Lighthouse, Nimbus, and Lodestar).

Every network's execution layer works with (and only with) its corresponding "partner" consensus layer. EL-CL network pairs work together to run Ethereum proof-of-stake.

<br />

<table>
    <tr>
        <th style={{minWidth: 160 + 'px'}}>EL network</th> 
        <th style={{minWidth: 160 + 'px'}}>CL network</th>
        <th>Description</th>
    </tr>
    <tr>
      <td>Mainnet</td>
      <td>Mainnet</td>
      <td>When people refer to Ethereum, they're usually referring to Ethereum Mainnet, which refers to a pair of networks: execution-layer (EL) Mainnet and consensus-layer (CL) Mainnet. CL Mainnet is commonly referred to as the Beacon Chain.<br/><br/>This network pair mints and manages real <strong>ETH</strong>.</td>
    </tr> 
    <tr>
      <td>Goerli</td>
      <td>Prater</td>
      <td>The Goerli-Prater pair is the test network that most people use when learning how to configure their validator for the first time. After Sepolia, Goerli-Prater will be Merge-tested.<br/><br/>This network pair mints and manages <strong>Goerli ETH</strong>, a type of testnet ETH used exclusively within this network pair.</td>
    </tr>
    <tr>
      <td>Sepolia</td>
      <td>Sepolia</td>
      <td>Consensus-layer Sepolia is a new network that was created to facilitate Merge testing, similar to consensus-layer Ropsten. Sepolia is the next network that will be Merge-tested. The <a href='../../install/install-with-script'>Prysm Quickstart</a> shows you how to configure a Merge-ready node on Sepolia. Note that this is a permissioned network, so you can run a node on Sepolia, but not a validator.<br/><br/>This network pair mints and manages <strong>SepplETH</strong>, a type of testnet ETH used exclusively within this network pair.</td>
    </tr>
    <tr>
      <td>Ropsten</td>
      <td>Ropsten</td>
      <td>Consensus-layer Ropsten is a new network that was created to facilitate Merge testing. This network pair was one of the first pairs that was Merge-tested (see <a href='https://www.youtube.com/watch?v=2OfRuKSPjjw'>Ethereum Merge: Stage 1 - Ropsten Network Upgrade</a> for a livestream of the event).<br/><br/>This network pair mints and manages <strong>Ropsten ETH</strong>, a type of testnet ETH used exclusively within this network pair.</td>
    </tr>
</table>



## Frequently asked questions

**Can I run an execution node without running a beacon node?**

No. Although this is possible pre-Merge, all Ethereum network participants will need to run both an execution node and a beacon node.

**What happened to miners?**

The concept of mining exists only in the domain of proof-of-work consensus. After The Merge, Ethereum's consensus will be managed by a proof-of-stake mechanism, which replaces miners with validators.

**Where do slashers come into play?**

Slashers, like validators, use specialized pieces of consensus-layer client software to fulfill a critical responsibility for the Ethereum network. Slashers attempt to detect and punish malicious validators. Learn more by reading our [Slasher documentation](../prysm-usage/slasher.md).

**How do I get testnet ETH?**

Your best bet is to ask the community for testnet ETH on either the [Prysm Discord server](https://discord.gg/prysmaticlabs) or on [r/ethstaker](https://www.reddit.com/r/ethstaker).