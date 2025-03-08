# Virtualized Secure Network with Splunk and Active Directory

This project demonstrates the creation and configuration of a secure network environment using **Splunk**, **Active Directory**, and **Atomic Red Team** to simulate, monitor, and detect security threats. The primary goal of this project is to set up a fully functional Active Directory environment, monitor endpoint activities using Splunk, and simulate various attack techniques to evaluate the effectiveness of the monitoring and detection tools. By leveraging **Splunk** for event aggregation, **Active Directory** for user management, and **Atomic Red Team** for attack simulations, this setup enhances the ability to monitor and respond to security incidents in real-time.

## Key Features

- **Splunk**: Used for ingesting and analyzing event data from Windows Server and Windows 10 machines. Splunk’s powerful search and reporting capabilities help detect suspicious activities and generate real-time alerts.
- **Active Directory**: Configured on a Windows Server to manage domain users and security policies. Active Directory was used to simulate a secure enterprise environment with controlled user access and authentication.
- **Atomic Red Team**: Provides a set of predefined attack simulations based on real-world tactics, techniques, and procedures (TTPs). These simulations help assess the network’s defense and the effectiveness of detection tools.
- **Kali Linux**: Used to perform brute force attacks against the domain user accounts to generate attack telemetry and test the response of the security monitoring tools.
- **Virtualized Network**: The project was implemented in a virtualized environment, with multiple virtual machines deployed using **Vultr**, which includes **Windows 10**, **Windows Server**, and **Kali Linux** to simulate a realistic network setup.

## Technologies Used:
- **Splunk**: For event aggregation, analysis, and detection of suspicious activity.
- **Active Directory**: For user and access management in a secure network environment.
- **Atomic Red Team**: For simulating attack techniques and testing defense mechanisms.
- **Kali Linux**: For performing simulated attacks to generate telemetry data for analysis.
- **Vultr**: For hosting the virtual machines that make up the network environment.

## Project Walk-through

### 1. Design Network Diagram for the Simulated Environment
The network diagram illustrates the architecture of the project, showing how the various systems and virtual machines (VMs) interact within the environment, including Splunk, Active Directory, and the endpoint machines.

![Network Diagram](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/Active%20Directory%20Project.drawio.png?raw=true)

### 2. Deploying Servers on Vultr
I used **Vultr** to set up the servers for the project, which host the various VMs, including **Windows 10**, **Windows Server**, and **Kali Linux**. These servers were configured to simulate a realistic network environment.

![Vultr Servers](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/VultrServers.jpeg?raw=true)

Additionally, I used a **VPC** (Virtual Private Cloud) to set up the networking, connecting all the VMs within the secure network environment.

![Vultr VPC](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/VultrVPC.jpeg?raw=true)

### 3. Installing and Configuring Sysmon on Windows Machines
Sysmon was installed on both **Windows 10** and **Windows Server** to monitor detailed system activities such as process creation, network connections, and file modifications.

![Sysmon Installation](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/Sysmon.jpeg?raw=true)

### 4. Installing and Configuring Splunk on Windows Machines
Splunk was set up on both **Windows 10** and **Windows Server** to gather and analyze event logs. The installation process was followed by configuring Splunk to aggregate logs from these servers.

![Splunk Installation](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/SplunkInstall.jpeg?raw=true)

After installation, the Splunk server was configured to ingest logs and analyze the data.

![Splunk Configuration](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/SplunkConfig.jpeg?raw=true)

![Splunk Forwarder Installation](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/SplunkForInstall.jpeg?raw=true)

### 5. Splunk Ingestion and Forwarding Configuration
Both **Windows 10** and **Windows Server** were configured to forward logs to the central Splunk server. This ensures that logs are collected and analyzed for security events.

![Windows 10 Forwarding Logs](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/TargetPC.jpeg?raw=true)

![Windows Server Forwarding Logs](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/ActDirServer.jpeg?raw=true)

Splunk is now successfully ingesting logs from both systems.

![Splunk Ingesting Logs](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/SplunkIngest.jpeg?raw=true)

### 6. Setting Up Active Directory on Windows Server
**Active Directory Domain Services** (AD DS) were installed on **Windows Server** and the server was promoted to a **Domain Controller** to manage user accounts, policies, and other network resources.

![Active Directory Installation](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/ADInstall.jpeg?raw=true)

Two users, **Terry Smith** and **Jenny Smith**, were created in Active Directory as part of the domain configuration.

![User Creation - Terry Smith](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/UserTerry.jpeg?raw=true)

![User Creation - Jenny Smith](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/UserJenny.jpeg?raw=true)

### 7. Configuring a Windows Machine to Join the Domain
The **Windows 10** machine was successfully joined to the **main.local** domain, making it part of the domain controlled by the **Active Directory** server.

![Domain Join Process](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/DomainJoin.jpeg?raw=true)

Once joined, I logged into the **Windows 10** machine using a domain user account.

![Domain Login](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/DomainLogin.jpeg?raw=true)

### 8. Performing a Brute Force Attack Using Kali Linux
A **brute force** attack was launched using **Kali Linux** against the domain accounts to generate telemetry data. This allowed for the analysis of attack patterns and behaviors in the following steps.

![Kali Brute Force Attack](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/KaliBruteForce.jpeg?raw=true)

### 9. Monitoring and Analyzing Attack Activity with Splunk
The brute force attack was logged by **Splunk**, capturing both the failed login attempts and the successful attack. I analyzed these logs to assess the system's response to suspicious activities.

![Brute Force Log in Splunk](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/BruteForceLog.jpeg?raw=true)

![Brute Force Detailed Log](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/BruteForceDetailLog.jpeg?raw=true)

### 10. Installing and Configuring Atomic Red Team for Attack Simulation
**Atomic Red Team** was used to simulate various attack techniques, such as **Mimikatz** and **BloodHound**, to evaluate the effectiveness of the detection tools and security defenses.

![Atomic Red Team Setup](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/AtomicTest1.jpeg?raw=true)

### 11. Running Atomic Red Team Tests and Detecting Malicious Activity in Splunk
The **Atomic Red Team** tests, including **Mimikatz** and **BloodHound**, were executed, and their results were captured in **Splunk**, confirming the system's ability to detect these simulated attack techniques.

![Atomic Red Team Test 2](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/AtomicTest2.jpeg?raw=true)

![Atomic Log 1](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/AtomicLog1.jpeg?raw=true)

![Atomic Log 2](https://github.com/sufani/Virutalized-Secure-Network-with-Splunk-and-Active-Directory/blob/main/images/AtomicLog2.jpeg?raw=true)
