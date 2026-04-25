<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1> Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Command-Line Tools
- Various Network Protocols (IMCP,SSH,DNS)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>The Set Up </h2>
I set up two virtual machines in Azure on the same virtual network so they could communicate with each other. One machine runs Windows 10 Pro, while the other runs Ubuntu. The Windows system connects to the Ubuntu machine using the command line/PowerShell.

<h2>Actions and Observations</h2>

<p>
<img width="1626" height="882" alt="image" src="https://github.com/user-attachments/assets/d791dab2-8d8a-4792-9ce7-7a3427af12f2"
/>

  
</p>
<p>
I used Remote Desktop Connection to access the Windows VM through its public IP address, then installed Wireshark to start analyzing network traffic.
</p>
<br />

<p>
<img width="1620" height="870" alt="image" src="https://github.com/user-attachments/assets/acad0f87-8f0e-41f7-8511-8a3124521d86"
/>
</p>
<p>
In Wireshark, I applied a filter for ICMP (Internet Control Message Protocol) traffic and used PowerShell to run the ping command. Ping relies on ICMP, which allows devices on a network to report communication issues. I tested connectivity by pinging the Ubuntu VM using its private IP address, as well as google.com. I then performed a continuous ping to the Ubuntu VM using ping -t (IP address) to observe how network security groups affect traffic.
</p>
<br />

<p>
<img width="1638" height="780" alt="image" src="https://github.com/user-attachments/assets/c9b6f2ab-708a-4161-9f31-de2c74fef9b6" />

</p>
<p>
In the Azure portal, I accessed the Ubuntu VM’s networking settings and created an inbound rule to block ICMP traffic. I assigned it a higher priority than the SSH rule (300) so it would take precedence.
</p>






<img width="1620" height="904" alt="image" src="https://github.com/user-attachments/assets/7e640c3d-94dc-414c-828a-ddf9049d3197" />

</p>
<p>
After returning to the Windows VM, I observed that ICMP traffic was blocked due to the inbound security rule. Once the rule was modified to allow traffic again, the continuous ping resumed without timing out.
</p>
<br />




<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
