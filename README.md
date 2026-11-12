# CN Skill 1 – Encapsulation Builder

## Aim
To capture and analyze network packets using Wireshark and understand the encapsulation process, including Ethernet, IP, TCP, and UDP headers, packet overhead, and network efficiency.

## Tools Used
- Wireshark
- Windows Operating System
- Internet connection

## Procedure

1. Installed and opened Wireshark.
2. Selected the active Wi-Fi network interface.
3. Started packet capture and generated network traffic by accessing websites.
4. Stopped the capture after collecting packets.
5. Applied display filters to identify different protocols:
   - `tcp` – Displays TCP packets.
   - `udp` – Displays UDP packets.
   - `icmp` – Displays ICMP packets.
   - `tcp.len > 0` – Displays TCP packets containing data.
6. Selected individual packets and expanded their protocol layers.
7. Inspected Frame, Ethernet II, IPv4, TCP, and UDP header information.
8. Saved the packet capture as `Encapsulation_Capture.pcapng`.

## Wireshark Packet Analysis

### 1. TCP Packet – Frame 44

| Parameter | Observed Value |
|---|---|
| Frame Number | 44 |
| Frame Length | 55 bytes |
| Ethernet Header Length | 14 bytes |
| IP Header Length | 20 bytes |
| IP Total Length | 41 bytes |
| TCP Header Length | 20 bytes |
| TCP Payload Length | 1 byte |
| Source IP | 10.250.29.80 |
| Destination IP | 35.190.80.1 |
| Source Port | 62966 |
| Destination Port | 443 |

**Calculation:**

- Ethernet Header = 14 bytes
- IP Header = 20 bytes
- TCP Header = 20 bytes
- TCP Payload = 1 byte

Total Frame Length = 14 + 41 = **55 bytes**

### 2. UDP Packet – Frame 41

| Parameter | Observed Value |
|---|---|
| Frame Number | 41 |
| Frame Length | 110 bytes |
| Ethernet Header Length | 14 bytes |
| IP Header Length | 20 bytes |
| IP Total Length | 96 bytes |
| UDP Header Length | 8 bytes |
| UDP Payload Length | 68 bytes |
| Source IP | 10.250.16.154 |
| Destination IP | 224.0.0.251 |
| Source Port | 5353 |
| Destination Port | 5353 |

**Calculation:**

- Ethernet Header = 14 bytes
- IP Header = 20 bytes
- UDP Header = 8 bytes
- UDP Payload = 68 bytes

Total Frame Length = 14 + 96 = **110 bytes**

## Observation Table

| Parameter | TCP (Frame 44) | UDP (Frame 41) |
|---|---:|---:|
| Frame Length | 55 bytes | 110 bytes |
| Ethernet Header | 14 bytes | 14 bytes |
| IP Header | 20 bytes | 20 bytes |
| Transport Header | 20 bytes | 8 bytes |
| IP Total Length | 41 bytes | 96 bytes |
| Payload Length | 1 byte | 68 bytes |

## Packet Overhead and Network Efficiency

Consider the following theoretical example:

- Ethernet Header = 14 bytes
- IPv4 Header = 20 bytes
- TCP Header = 20 bytes
- Application Data = 1500 bytes
- FCS = 4 bytes

**Total Frame Size:**

14 + 20 + 20 + 1500 + 4 = **1558 bytes**

**Total Overhead:**

14 + 20 + 20 + 4 = **58 bytes**

**Network Efficiency:**

Efficiency = (Application Data / Total Frame Size) × 100

= (1500 / 1558) × 100

= **96.28%**

Therefore, the network efficiency is approximately **96.28%**.

*Note: This is a theoretical calculation. Wireshark may not display the FCS field in every capture.*

## Answers to Questions

### 1. What is encapsulation?

Encapsulation is the process of adding protocol-specific headers (and sometimes trailers) to data as it moves through different layers of the network model.

### 2. What is the purpose of the Ethernet header?

The Ethernet header contains source and destination MAC addresses and the EtherType field. It helps deliver frames within a local network.

### 3. What information is stored in the IP header?

The IP header contains source and destination IP addresses, packet length, TTL, protocol information, and other fields required for packet delivery.

### 4. What is the difference between TCP and UDP headers?

TCP has a minimum header size of 20 bytes and provides reliable, connection-oriented communication. UDP has an 8-byte header and provides connectionless communication with lower overhead.

### 5. Why does each protocol add its own header?

Each protocol adds a header to provide the information required for its responsibilities, such as addressing, routing, sequencing, and error checking.

### 6. What is packet overhead?

Packet overhead refers to the additional bytes used by protocol headers and trailers rather than the actual application data.

### 7. How does header overhead affect network efficiency?

More header overhead increases the total packet size and reduces the percentage of bytes available for application data. This can reduce network efficiency.

## Screenshots

The following screenshots are included in the `screenshots` folder:

1. **TCP Packet Details** – `tcp-details.png`
2. **UDP Packet Details** – `udp-details.png`
3. **TCP and UDP Packet List** – `packet-list.png`

### TCP Packet Details
![TCP Packet Details](screenshots/tcp-details.png)

### UDP Packet Details
![UDP Packet Details](screenshots/udp-details.png)

### TCP and UDP Packet List
![TCP and UDP Packet List](screenshots/packet-list.png)

## Conclusion

Successfully captured and analyzed TCP and UDP packets using Wireshark. Inspected Ethernet, IPv4, TCP, and UDP headers and understood the encapsulation process. Also calculated packet overhead and network efficiency, gaining practical knowledge of how data is transmitted across networks.

---

**Project:** CN Skill 1 – Encapsulation Builder  
**Tool:** Wireshark  
**File:** `Encapsulation_Capture.pcapng`
