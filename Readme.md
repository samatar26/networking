# Networking

We'll be covering the following topics:
- Introduction to networking
- Network communication protocols
  - TCP/IP protocol, DHCP and DNS
- Network Topology
  - Star, Ring, Tree, Fully connected, etc.
- Network Types
  - Personal Area Network (PAN), Local Area Network (LAN), Campus Area Network (CAN), etc.

### What is networking?

Two or more `nodes` (e.g. computers) connected together by some means of communication so as to share or distribute resources.

Connection can be achieved by cables, radio signals, telephone lines, signals over power lines, optical signals, satellite communications, etc.

This concept extends from small local clusters of computers to the internet.

![image](https://user-images.githubusercontent.com/22747985/32137424-5e4311cc-bc17-11e7-8ac8-4d90b39cbbae.png)

### Method of communication - TCP/IP

To function as a network, nodes need to utilise a common method of communication. The de facto standard specification for communication is `TCP/IP` (Transmission Control Protocol/Internet Protocol).

TCP/IP is maintained by a global standards body called the `Internet Engineering Task Force (IETF)`. It's a large open international community of network designers, operators, vendors and researchers concerned with the evolution of the internet architecture and the smooth operation of the internet. It's open to any interested individual.

## The protocol stack

This is generally referred to as the four-layer model, although there are six components to it in this case.

The protocol stack provides layers of abstractions to the communication process so that a logical communication can be considered between nodes at each layer. Think in terms of a postal or courier service as an analogy. Standards define the protocol stack itself (RFC1122) and various protocols within the stack.

![image](https://user-images.githubusercontent.com/22747985/32137495-0ce65d96-bc19-11e7-9e81-99ab8eaf7088.png)

![image](https://user-images.githubusercontent.com/22747985/32137566-5fd9aaca-bc1a-11e7-959c-cc659c2e8c27.png)


### The Application layer
Examples of applications are web browsers, mail client, etc. Examples of application-layer protocols are:
- HTTP
- SMTP
- POP3
- FTP
- DNS

From an application (and user) perspective a communication channel is established between two network nodes, e.g. a mail client and mail server.
This requires the node's IP addressess and port number, i.e. a web server (HTTP) identified by port 80.

![image](https://user-images.githubusercontent.com/22747985/32341648-05e88146-bff6-11e7-8622-71b492336c84.png)


### The Transport layer
Makes use of two main protocols:
- TCP (Transmission Control Protocol)
- UDP (User Datagram Protocol)

#### TCP
- Connection-oriented service - information exchanged prior to message transfer. (Handshaking protocol).
- `Reliable` transport (flow control, sequence numbers).
- `Retransmission` of lost packets.
- `Congestion control` - Slows down the transmission process in case of congestion.
- Used for mail, remote terminal, web access, file transfer, etc.

###### There's a 3-way Handshaking phase:

![image](https://user-images.githubusercontent.com/22747985/32407692-7cb48a60-c184-11e7-833a-62b6ba44d39d.png)


###### Connection tear-down:

![image](https://user-images.githubusercontent.com/22747985/32407698-ad4a21d0-c184-11e7-90ec-2a3c1f86ae1d.png)

### User Datagram Protocol (UDP)
- Connectionless, unreliable service.
- No handshaking protocol required.
- No congestion control.
- One to many broadcasting.
- Used for media streaming, telephony, etc.

# Network Layer

- `Network service model` specifies end-to-end data transport between one network node and another.
- The paths between thes nodes are identified by the network layer `routing protocol`.
- Various protocols identified at the network layer, i.e. the `Internet Control Message Protocol` (ICMP) and arguably the most important netwrok layer protocol: the `Internet Protocol` (IP)

## IP addressing
`IPv4` is still the main addressing method.
- 32 bit (4 byte) address usually written in dotted-deminal notation, e.g. `192.168.1.10`.
- All global internet addresses should be unique.
- There's the potential for a total of 2^32 possible addresses and these are allocated to countries by `Internet Assigned Numbers Authority` (IANA).

#### Domain Name System (DNS)
- Hierarchical naming structure for `hostnames` and is the mapping of hostnames to IP addresses.
- Hostnames can be considered as leaves in the hierarchical domain name structure.
- Name hierarchy is from right to left.
- `Top level domain` (TLD), e.g. com, net, etc. and country indicators, e.g. uk, cn, au, etc. are administered by the `International Corporation for Assigned Names and Numbers` (ICANN)!
- Followed by Second Level Domain (SLD), etc.

_**DNS creates addresses that are comprehensible by humans.**_

#### Dynamic Host Configuration Protocol (DCHP)
- This allows for automatic allocation of IP addresses.
- Also identifies DNS server(s) and first-hop router.
- Can be part of private network assigning addresses within the private range (subject to masking).

## Link Layer
- This is the layer that communicates with the physical device (e.g. network adapter, Wi-Fi adapter).
- Communication from node to node using unique `Media Access Control` (MAC) addresses.
- MAC is a six byte address which implies that there are potential 2^48 different addresses that can be used.
- This address is assigned to the node's adapter.

# Network Topology
Network topology refers to the arrangement of various elements (i.e. nodes, connecting lines, etc.) of a communication network. There are different layouts that are used to describe the toplogy of a network. The most common are:
- Star network
- Ring network
- Tree network
- Fully connected network, etc.

## Star Layout

The star network is one of the most popular network topologies. All peripheral nodes are connected only to a central hub (core node).

![image](https://user-images.githubusercontent.com/22747985/32407875-17a6d1f2-c187-11e7-83d2-669cd856b608.png)

- Advantages
  - Failure of one node does not affect the other nodes
  - Mobility of devices is flexible (i.e. a node can be added or removed without affecting the network)
- Disadvantages
  - A hub failure would make the entire network collapse.
  - There's a high cost of building a star network



## Ring Layout
In the ring network, the nodes are connected only to the adjacent ones. 

![image](https://user-images.githubusercontent.com/22747985/32408019-3e56a852-c189-11e7-9405-aae7ca0b922f.png)

- Advantages
  - No central hub or core node needed, therefore the workload and services are handled from all the nodes.
  - Unidirectional connection of the layout facilitates the identification and isolation of failures and errors.
- Disadvantages
  - The failure of one node will affect the other nodes and certainly the network operation.
  - Mobility of devices isn't flexible (i.e. you cannot add or remove a node without affecting the functionality of the network).

## Tree Layout
The tree network arranges the network nodes in a hierarchical way, where there is a parent-child relation between the nodes. 

![image](https://user-images.githubusercontent.com/22747985/32408021-41a0562a-c189-11e7-90e6-360f1ec0cd56.png)

- Advantages
  - It's scalable as leaf nodes can accommodate more nodes in the hierarchical chain.
  - Other hierarchical networks are not affected if one of them gets damaged.
- Disadvantages
  - Failure of one node affects the nodes that belong to the same sub-tree structure.
  - Mobility of devices isn't really flexible (i.e. it depends on the node that's being added or removed).
  - It's expensive to build as huge cabling is required.

## Fully Connected Layout
In a fully-connected network, any two nodes of the network can bi-directionally communicate, as they are directly connected to each other. 

![image](https://user-images.githubusercontent.com/22747985/32408050-ad6e1fea-c189-11e7-98dc-2f0a81ca1cf5.png)

- Advantages
  - Data can be transmitted from different devices concurrently. This topology can handle high traffic.
  - Failure of one node won't affect the other nodes (at least not seriously)
- Disadvantages
  - Mobility of devices isn't flexible.
  - Expensive to build as huge cabling is required.
