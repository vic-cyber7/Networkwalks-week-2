<h1 align="left">🛡️ Penetration Testing & Security Assessment</h1>

### 🔍 FOOTPRINTING & SCANNING PHASES

> **Operator:** Falusi Victor  
> **Program:** Networkwalks Cybersecurity Intern (Batch B083)  
> **Target Scope:** Local LAN & Authorized Sandbox Environment

---

## 📋 Engagement Blueprint

<details>
<summary><b>Click to expand full assessment metadata</b></summary>

| Field | Details |
| :--- | :--- |
| **Assessment Date** | 25 September 2026 |
| **Authorization Status** | Written Permission Secured & Verified |
| **Primary Environments** | Kali Linux & Windows Host Systems |
| **Current Status** | In Progress (Phase 3–5 Active) |

</details>

---

## ⚡ Execution Roadmap

*   **[PHASE 1]** Reconnaissance & Footprinting — `COMPLETED`
*   **[PHASE 2]** Scanning & Network Discovery — `COMPLETED`
*   **[PHASE 3-5]** Vulnerability Assessment & Reporting — `IN PROGRESS`

---

## 🛠️ Completed Modules & Toolchain

### Modules Completed
*   `W2-PM1` — Multi-vector utility deployment via Kali Linux toolset.
*   `W2-PM5` — Host discovery and deep topology mapping using Zenmap.

### Operational Config
```yaml
operator: Falusi Victor
batch: B083 - Networkwalks
primary_platforms: [Kali Linux, Windows]
authorization: Verified Target (Local LAN)

```
1. # Liability Disclaimer

All activities were performed only on systems I own or had permission to access. This material is for educational and research purposes only and should be used responsibly in authorized environments.

Unauthorized access or misuse of these techniques may be illegal and can result in serious consequences. You are responsible for how you use this knowledge.

2. # Introduction

This report covers two Week 2 activities at Networkwalks: footprinting networkwalks.com using Kali Linux (W2-PM1) and scanning my local network using Zenmap (W2-PM5).

The activities demonstrate how public information can be gathered and how active hosts can be identified on a network. Each step includes the command used, results, screenshots, and a brief security note.

## 3. Tools Used

| Tool | Purpose |
|---|---|
| Kali Linux & Windows | Operating systems used for reconnaissance activities |
| WHOIS | Find domain registration details such as dates and name servers |
| WhatWeb | Identify web technologies, servers, CMS, plugins, and IP information |
| nslookup | Resolve the domain name to its IP address using DNS |
| curl -I | View the website's HTTP response headers |
| Wafw00f | Detect whether a Web Application Firewall (WAF) protects the site |
| DNSRecon | Enumerate DNS records such as NS, MX, SPF, TXT, and SRV |
| Zenmap (Nmap GUI) | Scan the local subnet to identify live hosts, IP addresses, and MAC addresses |

4. # Activities Performed
 ### 4.1 Footprinting & Reconnaissance 
 I performed reconnaissance against the networkwalks.com domain using six Kali Linux tools: 
 ```bash
whois
whatweb
nslookup
curl -I
wafw00f
dnsrecon
```
Each tool was used to collect a different type of information about the target.

### 4.1.1 WHOIS 
WHOIS to gather publicly available domain registration details, including the domain’s name servers and registration information. The results provided insight into the domain’s registration and hosting infrastructure.

### 4.1.2 WhatWeb
Used WhatWeb to identify the technologies and services running on the website. The results identified the technologies and services running on the website.
```
WordPress 7.0.4
WP Download Manager 3.3.58
````
### 4.1.3 Nslook 
Nslookup, I resolved the domain name to its IP address. The provided result identified 
```
192.232.216.135.
```
### 4.1.4 cURL 
I used **curl** with the `-I` option to view and analyze the website’s HTTP response headers. The following HTTP-header was used: 
```
curl -I networkwalks.com
```
This provided additional information about the web application and exposed the WordPress REST API endpoint
```
/wp-json/
```
### 4.1.5 Wafw00f
I used Wafw00f to determine whether a Web Application Firewall was protecting the website.The result identified:
```
ModSecurity (SpiderLabs)

```
### 4.1.6 DNSRecon 
Finally, I used DNSRecon to enumerate the domain’s DNS records. The results provided information about its DNS configuration and related records.
```
. Name servers
. Mail servers
. SPF/TXT records
. Service records
. DNS software information.
```
# 4.2 Network Scanning with Zenmap

For the second activity, I used **Zenmap** to perform network discovery on my local network. The exercise involved identifying my local IP address and subnet, discovering active hosts, recording their IP and MAC addresses, and creating a network topology.

I first used the Windows `ipconfig` command to find my local IP address and subnet. I then entered the subnet into Zenmap and selected **Ping Scan** to identify active hosts.
Example identified 
```
10.167.140.121
10.167.140.35
```
The example also identified with MAC addresses. 
 After completing the scan, I opened the **Topology** section in Zenmap, enabled the legend, and exported the network topology as a PDF as required by the practical task.
### Note: 
The actual subnet, number of hosts and addresses should be replaced with the results from my own network when submitting the report.

### 5. Risk Analysis & Impact 


| # | Risk / Finding | Evidence / Observation | Potential Impact | Risk Level |
|---|---|---|---|---|
| 1 | Web technology information exposed | WhatWeb identified WordPress and WP Download Manager | Could help an attacker identify the technologies in use and determine areas that may require further security assessment |🟡Medium |
| 2 | Server IP address identifiable | Nslookup resolved the domain to 192.232.216.135 | Provides information about the location of the web service and its hosting infrastructure |🟢 Low |
| 3 | HTTP technical information exposed | Curl returned HTTP response headers and exposed `/wp-json/` | Could assist with technology fingerprinting and further information gathering | 🟢Low |
| 4 | WAF technology identifiable | Wafw00f identified ModSecurity (SpiderLabs) | Provides insight into the web application's security controls and architecture | 🟢Low |
| 5 | DNS infrastructure information exposed | DNSRecon identified DNS, mail, and service-related records | Could help an attacker build a broader picture of the organization's infrastructure |🟡Medium |
| 6 | Multiple live hosts visible on local network | Zenmap identified four live hosts in the example network | Could help identify devices that may require further security review, especially if unauthorized devices are present |🟡Medium |

Risk level key:  🔴Critical 🟡 Medium  🟢Low

### Note: The risks above are observations from the footprinting and scanning exercises, not confirmed vulnerabilities.

The practical exercises focused mainly on **information gathering and host discovery**. No exploitation or vulnerability testing was carried out during these two modules.

Therefore, findings such as software versions, IP addresses, or DNS records do not necessarily indicate a vulnerability. Further **authorized security testing** would be needed to confirm whether any actual security weaknesses exist.
### 6. Recommendations 
Based on the findings from these activities, the following security improvements are recommended:

**1. Review publicly exposed technology information**
Organizations should regularly assess the information exposed about their web technologies, CMS platforms, and plugins.
**2. Keep software up to date**
CMS platforms, plugins, and other web technologies should be regularly updated and checked against current security advisories.
**3. Review HTTP Headers**
Regularly review HTTP response headers to identify and reduce unnecessary technical information exposure.

**4. Review DNS Records Regularly**
Periodically review DNS records to ensure that only necessary information and services are publicly accessible.

**5. Properly Configure and Monitor the WAF**
Keep the WAF (ModSecurity) enabled, properly configured, and monitored to help protect the web application.

**6. Perform Regular Internal Network Discovery**
Regularly scan internal networks to identify active devices and maintain visibility of connected systems.

**7. Investigate Unknown Devices**
Any unexpected devices discovered during network scans should be identified, verified, and investigated.

**8. Maintain Network Documentation**
Keep network topology and device information properly documented and updated as changes occur.

**9. Perform Security Testing with Authorization**
Reconnaissance and scanning activities should only be conducted on systems and networks where proper authorization has been obtained.

# 7. Conclusion

During Week 2 of my Cybersecurity & Ethical Hacking internship, I completed practical exercises covering **footprinting, reconnaissance, and network scanning**.

For the footprinting activity, I used six Kali Linux tools to gather information about the target domain. This helped me understand how **WHOIS, WhatWeb, Nslookup, Curl, Wafw00f, and DNSRecon** can be used to collect domain, web technology, HTTP, WAF, and DNS information.

For the network scanning activity, I used **Zenmap** to examine my local network, identify active hosts, collect IP and MAC address information, and create a network topology.

These exercises helped me understand how reconnaissance provides useful information about a target before further security assessment is carried out. I also gained more practical experience with cybersecurity tools and learned how to interpret and document their results.

Another important lesson was the value of **clear security reporting**. Documenting the tools used, observations, potential impact, and recommended actions makes technical findings easier to understand and review.

Overall, the activities improved my practical understanding of reconnaissance and network discovery and gave me more confidence in using these techniques in a controlled lab environment. All activities were performed within an **authorized educational scope**.

# 8. Evidences Collected
### Footprinting Evidence 
<details>
<summary>Click to view WHOIS Result</summary>

<img width="1280" height="800" alt="WHOIS Result" src="https://github.com/user-attachments/assets/56f2172b-e9e1-449b-b8de-e8ac3b2e8498" />

</details>

<details>
<summary>Click to view WhatWeb Result</summary>

<img width="1280" height="800" alt="WhatWeb Result" src="https://github.com/user-attachments/assets/c7c4a9fb-5c78-4324-8a3a-5841056035bf" />

</details>

<details>
<summary>Click to view Nslookup Result</summary>

<img width="1280" height="800" alt="Nslookup Result" src="https://github.com/user-attachments/assets/33c70070-5763-4d25-b6ab-c7e4df177d3b" />

</details>


<details>
<summary>Click to view Curl Result</summary>

<img width="1280" height="800" alt="Curl Result" src="https://github.com/user-attachments/assets/b20da618-c4c1-4669-9cb7-af2ed70ad2b3" />

</details>


<details>
<summary>Click to view Wafw00f Result</summary>

<img width="1280" height="800" alt="Wafw00f Result" src="https://github.com/user-attachments/assets/4420a7f2-2489-41e2-bcf7-95de4229537e" />

</details>

### Zenmap Evidence 
<details>
<summary>Click to view Zenmap Ping Scan Result</summary>

<img width="1920" height="1008" alt="Zenmap Ping Scan Result" src="https://github.com/user-attachments/assets/b3b6846d-9370-4f4e-8c3a-d4e1f70e75a7" />

</details>

<details>
<summary>Click to view Zenmap Host Discovery Result</summary>

<img width="1920" height="1008" alt="Zenmap Host Discovery Result" src="https://github.com/user-attachments/assets/9282457b-8b27-4956-84cd-2c4288d0f691" />

<details>
<summary>Click to view Zenmap Network Topology</summary>

<details>
<summary>Click to view Zenmap Network Topology</summary>

<img width="1920" height="1008" alt="Zenmap Network Topology" src="https://github.com/user-attachments/assets/7a90c3ff-2b29-4d4e-9790-6a210d9e3f20" />

</details>

# ### Knowledge Assessment

This practical assessed my ability to:

* Perform **network discovery and scanning** using Zenmap.
* Identify active hosts, IP addresses, MAC addresses, and detected services.
* Interpret and document **network scan results**.
* Create a basic **network topology** from scan results.
* Apply practical cybersecurity knowledge in an **authorized lab environment**.
* Provide **clear evidence** through screenshots and scan results.
* Maintain **professional documentation** of the activities, findings, and observations.
