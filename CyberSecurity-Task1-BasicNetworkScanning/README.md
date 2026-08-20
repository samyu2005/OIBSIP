# Task 1 – Basic Network Scanning with Nmap

## Objective

Perform a basic network scan on a local Windows machine using Nmap to identify open ports, running services, and the operating system, and document the security implications of the findings.

## Tools Used

- Nmap 7.99
- Windows Command Prompt
- Npcap

## Target

- Host: DESKTOP-QHOJI2T
- IP Address: 192.168.0.193
- Operating System: Microsoft Windows 10
- Scan Type: Local machine scan

## Nmap Installation

Nmap 7.99 was installed on the Windows system and verified using:

```text
nmap --version

The installed Nmap version and Npcap information were displayed successfully.

Scans Performed
1. Basic Network Scan

Command:

nmap 192.168.0.193

The scan identified the following open TCP ports:

Port	Service
135/tcp	msrpc
139/tcp	netbios-ssn
445/tcp	microsoft-ds
2869/tcp	icslap
3306/tcp	mysql
55555/tcp	unknown
2. Service Version Detection

Command:

nmap -sV 192.168.0.193

Detected services included:

Port	Service	Detection
135/tcp	msrpc	Microsoft Windows RPC
139/tcp	netbios-ssn	Microsoft Windows NetBIOS
445/tcp	microsoft-ds	Microsoft-DS
2869/tcp	http	Microsoft HTTPAPI httpd 2.0
3306/tcp	mysql	MySQL (unauthorized)
55555/tcp	unknown	Unknown
3. Operating System Detection

Command:

nmap -O 192.168.0.193

Nmap detected:

Device type: general purpose
Running: Microsoft Windows 10
OS CPE: cpe:/o:microsoft:windows_10
OS details: Microsoft Windows 10 1809 - 21H2
Network Distance: 0 hops
Security Analysis
Port 135 – MSRPC

Microsoft RPC is used by Windows components for remote procedure calls. Although it is a legitimate Windows service, unnecessary exposure of RPC services can increase the system's attack surface.

Port 139 – NetBIOS

NetBIOS Session Service is associated with Windows networking and file/printer sharing. It should generally be restricted to trusted networks because exposed NetBIOS services can reveal network information.

Port 445 – Microsoft-DS / SMB

Port 445 is commonly associated with SMB file and printer sharing. SMB should be restricted to trusted networks and kept updated because vulnerable SMB implementations have historically been targeted by malware.

Port 2869 – HTTP / Microsoft HTTPAPI

Nmap identified Microsoft HTTPAPI 2.0 and associated the service with SSDP/UPnP functionality. Unnecessary UPnP-related services should be disabled or restricted where they are not required.

Port 3306 – MySQL

Port 3306 is the standard port used by MySQL database servers. Nmap detected MySQL and reported it as "unauthorized", meaning Nmap could not authenticate to obtain further service information. This does not by itself indicate that the database is compromised.

Database services should be restricted to trusted hosts and should not be unnecessarily exposed to untrusted networks.

Port 55555 – Unknown

Nmap could not identify the service running on port 55555. An unknown open port should be investigated to determine which application is using it and whether the service is required.

Key Findings
Six open TCP ports were identified.
Windows networking services were detected.
A MySQL service was detected on port 3306.
Port 55555 was not identified by Nmap.
The target system was detected as Microsoft Windows 10.
The scan was performed on a locally owned machine for educational purposes.
Ethical Use

Network scanning must only be performed against systems that you own or have explicit permission to test.

This task was performed only on a local machine under authorized conditions. External, public, or production systems were not scanned.

Conclusion

Nmap successfully identified open ports, services, and the operating system of the local Windows machine. The results demonstrate how network scanning can help identify exposed services and understand a system's network attack surface.
