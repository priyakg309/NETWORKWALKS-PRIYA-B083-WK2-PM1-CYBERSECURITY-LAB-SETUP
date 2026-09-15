# networkwalks-B082-week2-PENETRATION-TESTING REPORT
<div align="center">

# 🔐 Cybersecurity PENETRATION-TESTING REPORT

**Building an isolated virtual lab for penetration testing and ethical hacking practice**
</div>

<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ver-Virtualbox%20v7.2-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Kali%20Linux-v2026.2-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Penetration%20Testing-C00000?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Virtualization-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
  <img src="https://img.shields.io/badge/Kali%20Linux-404040?style=flat-square&labelColor=C00000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/NetworkWalks-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ethical%20Hacking-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
</p>

## FOOTPRINTING & NETWORK SCANNING PHASES

## 👤 Penetration Testing Engagement Information
| Category                 | Details                                                  |
| ------------------------ | -------------------------------------------------------- |
| 👤 **Project Name**      | Penetration Testing Report                               |
| **Pentester Name**       | Priya Kishore Gehani                                     |
| **Role**                 | Cybersecurity Student / Junior Penetration Tester        |
| **Program / Batch**      | B083 – Networkwalks                                      |
| **Assessment Date**      | 18 September 2026                                        |
| **Assessment Type**      | Authorized Penetration Testing & Security Assessment     |
| **Client / Target**      | Networkwalks — Written Authorization Secured             |
| **Additional Target**    | Tester-Owned Local LAN Network                           |
| **Authorization Status** | ✅ Authorized — Written Permission Secured               |
| **Testing Environment**  | Controlled Cybersecurity Laboratory / Authorized Network |
| **Module 01**            | W2-PM1 — Multiple Kali Linux Tools                       |
| **Module 02**            | W2-PM5 — Zenmap Scanning                                 |
| **Phase 1**              | ✅ Completed — Reconnaissance & Footprinting              |
| **Phase 2**              | ✅ Completed — Scanning & Network Discovery               |
| **Phase 3**              | 🔄 In Progress — Enumeration & Service Analysis          |
| **Phase 4**              | ⏳ Pending — Vulnerability Assessment                     |
| **Phase 5**              | ⏳ Pending — Reporting, Risk Analysis & Recommendations   |


# 1. Liability Disclaimer

All activities documented in this project were conducted only on systems I own or have explicit written authorization to test. This repository is intended strictly for educational, research, and authorized cybersecurity purposes.

Unauthorized access or misuse of these techniques may violate applicable laws and result in serious legal or professional consequences. Users are solely responsible for how they apply this information.

# 2. Introduction

This penetration-testing report documents two key activities completed during **Week 2 of my ongoing cybersecurity internship program at Networkwalks**. The first activity focuses on the **footprinting and reconnaissance of the `networkwalks.com` domain** using multiple Kali Linux tools as part of **W2-PM1 (Multiple Kali Tools)**. The second activity focuses on **network scanning and host discovery of my own local network** using Zenmap as part of **W2-PM5 (Zenmap Scanning)**.

These two modules represent important stages of a structured penetration-testing methodology. The footprinting activity demonstrates how publicly available information can be collected and analyzed during the reconnaissance phase, while the Zenmap activity demonstrates how an authorized tester can identify live hosts and map the accessible network environment during the scanning phase. Together, these exercises provide practical insight into how a security assessment progresses from **initial information gathering and attack-surface identification to network discovery and analysis**.

All footprinting activities were performed using **Kali Linux**, while the authorized local-network scanning activity was conducted on a **Windows PC with Zenmap installed**. The testing activities were performed only against systems and networks that were within the defined and authorized scope of the assessment.

For transparency and reproducibility, each section of this report documents the **exact command or procedure used, the observed result, supporting screenshot evidence, and a brief security analysis** explaining the relevance of the finding from a penetration-testing perspective. This documentation is intended to demonstrate not only the technical execution of the exercises but also the reasoning behind each step and its importance in identifying potential security exposure.


## 3. Tools Used 
The table below lists each tool used in this report and its purpose.
|  # | Tool / Operating System  | Purpose / Function                                                                                                   |
| -: | ------------------------ | -------------------------------------------------------------------------------------------------------------------- |
|  1 | **Kali Linux & Windows** | Operating systems used for reconnaissance activities                                                                 |
|  2 | **WHOIS**                | Identifies domain registration details, including owner information, registration/expiration dates, and name servers |
|  3 | **WhatWeb**              | Fingerprints web technologies in use, such as server type, CMS, plugins, and IP address                              |
|  4 | **nslookup**             | Resolves the target domain name to its corresponding IP address via DNS                                              |
|  5 | **curl -I**              | Retrieves and displays the HTTP response headers of the target website                                               |
|  6 | **Wafw00f**              | Detects the presence of a Web Application Firewall (WAF) protecting the site                                         |
|  7 | **DNSRecon**             | Enumerates DNS records, including NS, MX, SPF, and TXT entries                                                       |
|  8 | **Zenmap (Nmap GUI)**    | Scans the local subnet to identify live hosts, their IP addresses, and MAC addresses                                 |
|  9 | **Windows CMD**          | Used for local IP address and MAC address identification                                                             |


## 4. Activities Performed

## 4.1 Footprinting & Reconnaissance

As part of the reconnaissance phase, I conducted an authorized footprinting assessment of the **networkwalks.com** domain using six Kali Linux tools: **WHOIS, WhatWeb, Nslookup, cURL, Wafw00f, and DNSRecon**. Each tool was selected to collect a specific category of publicly accessible information and to build a broader understanding of the target’s domain, web technologies, DNS configuration, and security infrastructure.

First, I used **WHOIS** to gather publicly available domain-registration information and identify the domain’s associated name servers. The results provided useful information regarding the domain registration and elements of its hosting and DNS infrastructure.

I then used **WhatWeb** to identify the technologies and components exposed by the target website. The results identified **WordPress 7.1** and **WP Download Manager 3.3.58**, along with additional technology-related information revealed by the website. Such information can help a security professional understand the target’s technology stack and identify areas that may require further security assessment.

Using **Nslookup**, I performed DNS resolution for the target domain to determine its associated IP address. The observed result resolved **networkwalks.com** to **192.232.216.135**. This information provides an important reference point for understanding the target’s publicly accessible network infrastructure.

Next, I used **cURL with the `-I` option** to inspect the HTTP response headers returned by the web server. The response provided additional information about the web application and revealed the presence of the **WordPress REST API endpoint `/wp-json/`**. HTTP headers and publicly accessible endpoints can provide useful information during reconnaissance and may help identify technologies or interfaces that should be reviewed during subsequent security-testing phases.

I also used **Wafw00f** to determine whether a **Web Application Firewall (WAF)** was present in front of the target website. The results identified **ModSecurity (SpiderLabs)** as the detected WAF technology. Identifying defensive technologies is an important part of reconnaissance because it helps a security assessor understand the protective controls implemented around the web application.

Finally, I used **DNSRecon** to perform DNS enumeration and collect additional publicly accessible DNS information. The results included details related to **name servers, mail servers, SPF/TXT records, service records, and DNS software information**. This information contributes to a more complete understanding of the target’s DNS architecture and externally visible infrastructure.

Overall, these reconnaissance activities provided a structured overview of the target’s **domain information, DNS configuration, web technologies, HTTP responses, publicly exposed endpoints, and security controls**. The collected information can serve as a foundation for the subsequent phases of an authorized penetration-testing assessment, particularly **scanning, enumeration, vulnerability assessment, and risk analysis**.

## 4.2 Network Scanning with Zenmap

As part of the second practical activity, I used **Zenmap**, the graphical interface for Nmap, to perform authorized network discovery within my **local LAN environment**. The primary objective of this activity was to identify the local network configuration, discover active hosts, determine their corresponding IP and MAC addresses where available, and visualize the discovered network through Zenmap’s topology feature.

I began by using the Windows **`ipconfig`** command to identify the system’s local IP address, subnet information, and network configuration. Based on the identified LAN subnet, I configured the appropriate network range as the target in Zenmap.

I then selected the **Ping Scan** profile in Zenmap to perform host discovery. This scan was used to determine which systems were actively responding within the authorized local network without performing an extensive service or vulnerability assessment.

The practical example identified the following four live hosts:

* **10.0.0.1**
* **10.0.0.2**

The example results also displayed corresponding **MAC addresses** for the discovered hosts, where the required network information was available. IP and MAC address information is useful for distinguishing individual devices and understanding the structure of a local network.

After completing the host-discovery scan, I reviewed the results within Zenmap and opened the **Topology** section to visualize the discovered network environment. I enabled the topology legend to make the resulting diagram easier to interpret and then exported the network topology in **PDF format**, as required by the practical exercise.

This activity provided practical experience with **local network discovery, live-host identification, IP/MAC address analysis, and network-topology visualization** using Zenmap. It also demonstrated how network scanning can be used as an initial step in an authorized penetration-testing workflow to establish an understanding of the systems present within a defined network scope.

> **Note:** The IP addresses, subnet, number of discovered hosts, MAC addresses, and topology shown in this section should reflect the **actual results obtained from my own authorized network during the assessment**. Any example values should be replaced with the corresponding evidence from the completed scan before final submission.

 # 5. Risk Analysis / Impact

Based on the information collected during the footprinting, reconnaissance, and network-scanning activities, I identified the following potential security observations and associated risks. These findings are intended to highlight information exposure and areas that may warrant further security review during subsequent phases of an authorized penetration test.

|  # | Finding                                             | Evidence / Observation                                                                      | Potential Impact                                                                                                                                        |   Risk Level  |
| -: | --------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----------: |
|  1 | **Web Technology Information Disclosure**           | WhatWeb identified **WordPress** and **WP Download Manager** technologies.                  | Disclosure of web technologies may assist attackers in fingerprinting the application and identifying components that require security review.          | 🟠 **Medium** |
|  2 | **Publicly Identifiable Server IP Address**         | `nslookup` resolved the target domain to `192.232.216.135`.                                 | Revealing the server's IP address provides information about the network infrastructure hosting the web service and may support further reconnaissance. |   🟢 **Low**  |
|  3 | **HTTP Response Header Information Disclosure**     | `curl -I` retrieved HTTP response headers and identified the `/wp-json/` endpoint.          | Exposed HTTP and application information may facilitate technology fingerprinting and additional enumeration activities.                                |   🟢 **Low**  |
|  4 | **WAF Technology Disclosure**                       | Wafw00f identified **ModSecurity (SpiderLabs)** as the Web Application Firewall technology. | Disclosure of security technologies may provide attackers with information about the application's defensive architecture.                              |   🟢 **Low**  |
|  5 | **DNS Infrastructure Information Disclosure**       | DNSRecon identified DNS, mail, and other service-related DNS records.                       | Exposed DNS information can assist in building a broader profile of the organization's network and service infrastructure.                              | 🟠 **Medium** |
|  6 | **Multiple Live Hosts Identified on Local Network** | Zenmap identified **four live hosts** within the authorized example network.                | Unidentified or unauthorized devices on the network may increase the potential attack surface and should be reviewed by the network administrator.      | 🟠 **Medium** |

| Risk Level    | Description                                                                      |
| ------------- | -------------------------------------------------------------------------------- |
| 🔴 **High**   | Significant security concern requiring prompt remediation                        |
| 🟠 **Medium** | Moderate security concern that should be addressed as part of security hardening |
| 🟢 **Low**    | Low-impact finding that should be considered for security improvement            |


The risks identified above represent observations from the footprinting, reconnaissance, and scanning exercises rather than confirmed vulnerabilities. The practical exercises primarily focused on information gathering, technology identification, DNS enumeration, and live-host discovery. No exploitation or vulnerability validation was performed as part of these two modules.

Therefore, the presence of information such as a software version, IP address, HTTP endpoint, WAF technology, or DNS record does not by itself indicate that the associated system is vulnerable. These findings should be considered potential areas for further investigation rather than confirmed security weaknesses.

Further authorized security testing and vulnerability validation would be required to determine whether any of the identified observations could lead to an actual security vulnerability or meaningful business impact.

 # 6. Recommendations

Based on the findings from these activities, the following security improvements are recommended:

|  # | Recommendation                                         | Justification                                                                                                                                                                                                                                          |
| -: | ------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
|  1 | **Review Publicly Exposed Technology Information**     | Organizations should regularly assess publicly discoverable information about web technologies, CMS platforms, plugins, and frameworks. Minimizing unnecessary technology disclosure can reduce opportunities for fingerprinting and targeted attacks. |
|  2 | **Keep Software Up to Date**                           | CMS platforms, plugins, frameworks, and other web technologies should be regularly updated and reviewed against current security advisories. Timely patching helps reduce exposure to known vulnerabilities.                                           |
|  3 | **Review HTTP Response Headers**                       | HTTP response headers should be periodically reviewed to identify unnecessary technical information. Removing non-essential details can make technology fingerprinting more difficult and reduce information leakage.                                  |
|  4 | **Review DNS Records Regularly**                       | DNS records should be audited periodically to verify that only required services and information are publicly exposed. Maintaining accurate DNS records helps reduce unnecessary infrastructure disclosure.                                            |
|  5 | **Properly Configure and Monitor the WAF**             | The **ModSecurity Web Application Firewall (WAF)** should remain enabled, properly configured, and actively monitored. Regular tuning and monitoring can strengthen the application's baseline protection against common and automated attacks.        |
|  6 | **Perform Regular Internal Network Discovery**         | Organizations should conduct periodic authorized network discovery to maintain visibility into active hosts, devices, and services. This helps identify unexpected systems and potential changes to the internal attack surface.                       |
|  7 | **Investigate Unknown Devices**                        | Any unexpected or unrecognized device discovered during authorized network scanning should be investigated and validated against approved asset inventories to determine whether it is legitimate.                                                     |
|  8 | **Maintain Accurate Network Documentation**            | Network topology diagrams, device inventories, IP allocations, and system ownership information should be kept accurate and up to date. Proper documentation supports effective monitoring, troubleshooting, and incident response.                    |
|  9 | **Conduct Security Testing with Proper Authorization** | Reconnaissance and scanning activities should only be performed against systems and networks for which explicit authorization has been granted. This ensures that security assessments remain controlled, ethical, and within the approved scope.      |


# 7. Conclusion

During **Week 2 of my Cybersecurity & Ethical Hacking internship at Networkwalks**, I completed practical activities focused on **footprinting, reconnaissance, and network scanning**. These exercises provided hands-on experience with important early stages of the penetration-testing methodology and helped me understand how security professionals systematically collect, analyze, and document information about an authorized target environment.

During the **footprinting and reconnaissance activity**, I used six Kali Linux tools—**WHOIS, WhatWeb, Nslookup, cURL, Wafw00f, and DNSRecon**—to collect and analyze publicly accessible information associated with the target domain. Through this activity, I learned how WHOIS can provide domain and registration-related information, WhatWeb can identify web technologies and components, Nslookup can perform DNS resolution, cURL can be used to inspect HTTP response headers, Wafw00f can identify the presence of a Web Application Firewall, and DNSRecon can provide additional information about DNS records and infrastructure.

In the **network-scanning activity**, I used **Zenmap** to analyze my authorized local network configuration and identify active hosts within the defined network range. I also gained practical experience in reviewing available **IP and MAC address information** and generating a visual **network topology** to better understand the structure of the discovered environment.

These exercises demonstrated that **information gathering is a fundamental component of cybersecurity and penetration testing**. Even before conducting vulnerability assessment or exploitation activities, a security professional can obtain valuable insights by systematically analyzing publicly available information, DNS records, web responses, technologies, and network behavior. Proper reconnaissance can therefore help establish an understanding of the target’s attack surface and guide subsequent security-assessment activities.

Another important lesson from this project was the value of **clear and structured security documentation**. A professional penetration-testing report should clearly describe what was performed, what was discovered, why the observation is relevant, what potential security impact it may have, and what recommendations can be implemented to reduce the associated risk.

Finally, this project reinforced the importance of **ethical and authorized security testing**. Reconnaissance, scanning, enumeration, and other penetration-testing activities must always be conducted within an approved scope and with appropriate authorization. All activities documented in this project were performed as part of the assigned educational cybersecurity exercises and within the defined testing scope.

Overall, Week 2 provided valuable practical exposure to the initial stages of penetration testing and strengthened my understanding of **reconnaissance, network discovery, security analysis, risk identification, and professional cybersecurity reporting**.

## 👤 Author
Priya Kishore Gehani

Cybersecurity Professional B083

LinkedIn: www.linkedin.com/in/priyagehani30

## 📌 Project Information

Program Name: Cybersecurity program at Networkwalks | Week: 02 | Repository: GitHub
