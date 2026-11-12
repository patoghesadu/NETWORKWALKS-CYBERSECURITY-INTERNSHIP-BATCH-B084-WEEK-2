# NETWORKWALKS-CYBERSECURITY-INTERNSHIP-BATCH-B084-WEEK-2
WEEK 2: FOOTPRINTING, RECONNAISSANCE &amp; NETWORK SCANNING REPORT Prepared by: Patrick Adu  Programme: NetworkWalks Cybersecurity Internship Batch: B084 Practical Exercises: W2-PM1 and W2-PM5

## 1. LIABILITY DISCLAIMER
I have performed these activities only on the systems & devices where I had secured written permission or the devices/systems that I own myself. All these materials are for education and research purpose only. Do not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorised access is a crime even when nothing is damaged.


## 2. INTRODUCTION

This report covers footprinting of the networkwalks.com domain using different Kali Linux tools and scanning my own local network with Zenmap. The practical exercise is divided into two main sections: footprinting and network scanning. Both activities helped me understand how attackers gather publicly available information about a target and identify active devices within a network.
This exercise forms part of Week 2 of my ongoing internship programme at Networkwalks.
All practical activities were carried out using Kali Linux for footprinting and a Windows PC with Zenmap installed for network scanning. For each task, I documented the exact commands used, the results obtained, supporting screenshots, and brief explanations of what each finding means from a cybersecurity and attacker's perspective.


This week's practical exercises focused on two areas:

- **W2-PM1 – Multiple Kali Linux Tools:** Using different reconnaissance tools to gather domain information, identify web technologies, inspect HTTP headers, and perform DNS enumeration.
- **W2-PM5 – Network Scanning with Zenmap:** Discovering devices on a local network, verifying active hosts, identifying available MAC address information, and inspecting network topology.

The exercises provided hands-on experience with commonly used cybersecurity tools and techniques.

## 3. TOOLS USED

| Tool                   | Purpose                                  |
| ---------------------- | ---------------------------------------- |
| Kali Linux             | Testing environment                      |
| WHOIS                  | Domain registration information          |
| WhatWeb                | Web technology identification            |
| Nslookup               | DNS information gathering                |
| cURL                   | HTTP response header inspection          |
| WAFW00F                | Web Application Firewall detection       |
| DNSRecon               | DNS enumeration                          |
| Zenmap                 | Graphical network scanning interface     |
| Nmap                   | Network discovery and scanning           |
| Windows Command Prompt | Network configuration and ARP inspection |

## 4. ACTIVITIES PERFORMED

### 4.1 FOOTPRINTING & RECONNAISSANCE (W2-PM1)

**Target Domain:** `networkwalks.com`

The following tools were used to gather information about the specified domain.

#### 4.1.1 WHOIS networkwalks.com

**Command:**

```bash
whois networkwalks.com
```

**Purpose:** Retrieve available domain registration information.

**Evidence – WHOIS&#x20;**&#x6E;etworkwalks.com

<img width="649" height="397" alt="whois" src="https://github.com/user-attachments/assets/bf065052-b312-45ae-821f-0aa07a3d0b76" />


#### 4.1.2 Web Technology Identification

**Command:**

```bash
whatweb https://networkwalks.com
```

**Purpose:** Identify technologies and web components exposed by the website.

**Evidence – WhatWeb**
<img width="629" height="155" alt="whatweb" src="https://github.com/user-attachments/assets/97675564-ad3e-4eaf-9e73-328622f619e7" />



#### 4.1.3 DNS Lookup

**Command:**

```bash
nslookup networkwalks.com
```

**Purpose:** Query DNS and retrieve available name resolution information.

**Evidence – Nslookup**

<img width="635" height="80" alt="nslookup" src="https://github.com/user-attachments/assets/d967ebbd-7d30-49a3-8b54-0c7638656036" />


#### 4.1.4 HTTP Response Header Inspection

**Command:**

```bash
curl -I https://networkwalks.com
```

**Purpose:** Retrieve HTTP response headers and inspect information returned by the web server.

**Evidence – curl -I**
<img width="634" height="131" alt="curl -I" src="https://github.com/user-attachments/assets/3701dd85-a8c4-4ff6-af7a-b029c62af0dc" />



#### 4.1.5 Web Application Firewall Detection

**Command:**

```bash
wafw00f https://networkwalks.com
```

**Purpose:** Check for indications of Web Application Firewall protection.

**Evidence – WAFW00F**
<img width="633" height="103" alt="wafw00f" src="https://github.com/user-attachments/assets/22697721-a81b-4391-bb6c-b195bf963bc3" />



#### 4.1.6 DNS Enumeration

**Command:**

```bash
dnsrecon -d networkwalks.com
```

**Purpose:** Gather additional DNS-related information about the specified domain.

**Evidence – dnsrecon -d**
<img width="546" height="209" alt="Dnsrecon" src="https://github.com/user-attachments/assets/bd65c9e4-4983-489b-80c9-02d92b290586" />



**Observations:**

The tools provided different perspectives on the target domain, including registration information, web technology fingerprints, DNS records, HTTP response headers, and possible WAF identification.

The actual outputs and findings will be interpreted based on the collected evidence.

### 4.2 NETWORK SCANNING WITH ZENMAP (W2-PM5)

**Objective:** Discover devices on my local network, verify their availability, inspect IP-to-MAC address information, and examine network topology.

#### 4.2.1 Local Network Configuration

I used the Windows Command Prompt to identify my local network configuration.

**Command:**

```cmd
ipconfig
```

**Network Details:**

| Parameter          | Value             |
| ------------------ | ----------------- |
| Local IPv4 Address | `192.168.52.1`  |
| Subnet Mask        | `255.255.255.0`   |


#### 4.2.2 Initial Network Discovery

I opened Zenmap, selected the **Ping Scan** profile, and entered my local network range.

**Command:**

```bash
nmap -sn 192.168.51.1/24
```

#### 4.2.3 Individual Host Verification

To verify the known devices, I performed individual scans.

**Default Gateway:**

```bash
nmap -sn 192.168.52.1
```
<img width="400" height="347" alt="Zenmap Task 3" src="https://github.com/user-attachments/assets/9f446008-e4c3-409b-ad0c-292b9f45ce42" />

**Local Windows Computer:**

```bash
nmap -sn 192.168.52.1
```

**Result:** Host reported as up.

**Evidence – Local Computer Scan**
<img width="400" height="347" alt="Zenmap Task 3" src="https://github.com/user-attachments/assets/9bc5bd1f-3645-4d3e-8b0a-89900f9c56dc" />



#### 4.2.4 Combined Host Discovery

I performed a combined scan against both verified IP addresses.

**Command:**

```bash
nmap -sn 192.168.52 192.168.52.254
```

Both hosts were reported as up and appeared in the Zenmap Hosts tab.

| IP Address       | Device                 | Status |
| ---------------- | ---------------------- | ------ |
| `192.168.52.1` | Local Windows computer | Up     |

**Evidence – Combined Scan**

<img width="1600" height="816" alt="combined.png" src="https://github.com/user-attachments/assets/9d764c36-18b0-4d0a-aa9b-0308292631be" />



#### 4.2.6 Network Topology Inspection

I inspected the Topology tab in Zenmap after performing the scans. However, both verified devices were not displayed together in the topology visualization.

The following simplified diagram represents the two verified devices and their network context. It is not a complete physical network map.



**Evidence – Zenmap Topology View**
<img width="505" height="401" alt="Zenmap Topology" src="https://github.com/user-attachments/assets/a299b601-baba-436e-9fa5-50779fb98347" />



The combined scan was also saved in pdf format for record keeping.

## 5. RISK ANALYSIS / IMPACT

The practical exercises demonstrated how reconnaissance and network discovery can support an initial security assessment.

Key observations include:

- Domain registration and DNS information can reveal publicly available infrastructure details.
- Technology fingerprinting can help identify the technologies exposed by a website.
- HTTP response headers can provide useful information about server configuration.
- WAF detection can indicate the presence of web application protection mechanisms.
- Network discovery and ARP inspection can help identify devices and their network information.

The initial network scan produced an anomalous result of 256 hosts reported as up. Further verification confirmed two specific hosts, so the initial count was not treated as a reliable device count.

No exploitable vulnerability is claimed solely from these discovery activities.

## 6. RECOMMENDATIONS

Based on the findings from the exercises, I identified some areas where security could be improved. The following recommendations can help organisations better protect their systems, websites, and networks.
1.	Review Information Exposed Online
Organisations should regularly check the information their websites reveal about the technologies, CMS platforms, and plugins they use. This helps reduce unnecessary exposure to potential attackers.
2.	Keep Software and Applications Updated
Websites, CMS platforms, plugins, and other software should be updated regularly to fix known security issues and protect against newly discovered vulnerabilities.
3.	Check HTTP Security Headers
Organisations should review their HTTP response headers to ensure they are not revealing unnecessary technical details that could make it easier for attackers to understand their systems.
4.	Regularly Review DNS Records
DNS records should be checked from time to time to ensure that only necessary information and services are publicly accessible.
5.	Ensure Proper WAF Configuration and Monitoring
The Web Application Firewall (ModSecurity) should remain enabled and properly configured. Its rules should also be reviewed and updated regularly to help detect and block suspicious activities.
6.	Carry Out Regular Network Scanning
Organisations should occasionally scan their internal networks to identify connected devices and have a clear understanding of what is running on their network.
7.	Investigate Unrecognised Network Devices
Any unfamiliar or unexpected device discovered during a network scan should be checked to confirm whether it is authorised to connect to the network.
8.	Keep Network Documentation Up to Date
Network diagrams, device details, and other important infrastructure information should be properly documented and updated whenever changes are made.
9.	Always Obtain Permission Before Security Testing
Footprinting, reconnaissance, and network scanning should only be performed on systems and networks where proper authorisation has been granted.
These recommendations highlight the importance of regular security checks, proper network management, and responsible use of cybersecurity tools.


## 7. CONCLUSION

Week 2 of my Cybersecurity and Ethical Hacking internship was an interesting learning experience. I spent the week getting hands-on experience with footprinting, reconnaissance, and network scanning.
I started with footprinting, where I used six Kali Linux tools to gather information about a target domain. I explored how WHOIS helps retrieve domain details, WhatWeb identifies the technologies behind a website, Nslookup checks domain names, Curl examines HTTP headers, Wafw00f detects web application firewalls, and DNSRecon provides more detailed DNS information.
Next, I moved on to network scanning using Zenmap. With this tool, I was able to examine my local network, identify devices that were active, collect their IP and MAC addresses, and create a network topology to better understand how devices were connected.
One thing that stood out to me during these exercises was how much information can be gathered about a system without actually attempting to break into it. I realised that understanding a target environment is one of the first and most important steps in cybersecurity. The information collected during reconnaissance can help security professionals identify weaknesses and better understand potential security risks.


**Prepared by:** Patrick Adu
**NetworkWalks Cybersecurity Internship — Batch B084**

*Learning through practical exercises, documenting findings, and building cybersecurity skills.*
