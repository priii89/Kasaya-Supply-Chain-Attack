# Kasaya-Supply-Chain-Attack

## Background
On July 2, 2021, hundreds of companies using Kaseya Virtual System Administrator (VSA) as their client IT management product,  became the victims of an extensive ransomware attack that hijacked and used Kaseya’s vulnerability to send a malicious script to all the end clients and encrypt their systems. 
https://www.tenable.com/blog/cve-2021-30116-multiple-zero-day-vulnerabilities-in-kaseya-vsa-exploited-to-distribute-ransomware
https://www.reuters.com/technology/200-businesses-hit-by-ransomware-following-incident-us-it-firm-huntress-labs-2021-07-02/
Kaseya clients from large enterprises to small companies across 17 countries had been hit by this devastating supply chain attack before they could even get a warning. The Swedish supermarket giant Coop had the worst hit by having to shut 800 of its stores worldwide. Also, in New Zealand, many kindergartens and schools had to be knocked offline.
This sophisticated attack was developed by REvil, one of the most powerful ransomware-as-a-service (RaaS) that develops ransomware payloads and provides the victims with decryption tools after getting paid. For revealing a universal decryption key, The REvil claimed to demand $70 million dollars and guaranteed that all victimized companies would be able to recover their files.
https://www.techrepublic.com/article/kaseya-supply-chain-attack-impacts-more-than-1000-companies/
Since Managed Service providers(MSPs) are usually less mature businesses they have weak unsecured programs. These companies, by leveraging Kaseya’s software, make it an irresistible and easy to exploit target in extortionists’ eyes.

#### Kaseya Virtual System Administrator (VSA)
Kaseya VSA is a remote monitoring and management (RMM) software that helps MSPs increase profitability. Moreover, it helps IT departments to get the most out of what they do. It boosts up IT teams by getting rid of inefficiency with an all-in-one endpoint management so they can progress even more than before. Managed Service Providers (MSPs) benefit from this program to remotely control and administer IT services demanded by customers. 
https://www.kaseya.com/products/vsa/

#### MSP = managed service provider (MSP)
MSP is a third-party company that remotely manages a customer's information technology (IT) infrastructure and end-user systems. MSP’s services may include network and infrastructure management, security and monitoring.

## Attack Overview
This attack impacted Kaseya customers who used the on-premise VSA server. The VSA server is typically used by MSPs to handle all of their clients and is used to manage huge fleets of computers. As illustrated below in fig.1, all client environments are not separated, so, if the VSA server is compromised, all client environments handled by this server are also vulnerable.
Furthermore, if the VSA server is connected to the internet, any vulnerability could be exploited to gain access to the server. 
A zero-day vulnerability in the VSA server was discovered and exploited by the threat actor, an affiliate of the REvil ransomware-as-a-service. A zero-day vulnerability is a defect in software or a network that hasn't been fixed or for which there isn't a patch. The vendor of the programme or device may or may not be aware of the problem. When a defect is publicly disclosed, it increases the danger of cyberattacks against businesses that use the software or device. 
The vulnerability was used to send a malicious script to all computers managed by the server, therefore reaching all of the end users. The script infected computers with the REvil malware and encrypted them.
![Overview of the attack](images/image1-edited.jpg)


            
## How the Kaseya VSA Zero-Day Exploit Worked
The pre-auth remote code execution exploit against Kaseya VSA Server that was exploited in the widespread Revil ransomware attack on July 2, 2021 is described as follows. Following the validation of the patch and confirmation that the attack vector is no longer active. The exploit took advantage of four vulnerabilities in the Kaseya programme, which were chained together as shown in the figure below:


![](images/image2-edited.jpg)

In the next section we will focus on the high-level steps of the exploit and describe steps 1 through 4 in detail:

### Step 1 – Bypassing Authentication [CWE-304]

The threat actor first sent a POST request to the resource /dl.asp with the POST data userAgentGuid=guid.


