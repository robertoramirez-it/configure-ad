<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This project outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Prepare Active Directory Infrastructure in Azure (VMs, DNS configuration)
- Deploy Active Directory (Assign admins/properties)
- Automate mass user creation using Powershell ISE
- Group Policy and File Permissions Management

<h2>Deployment and Configuration Steps</h2>

![virtual machines](https://github.com/user-attachments/assets/e59cbc10-7982-4e9f-9b4c-84c7bc8f4ba9)

<p>
To initiate the project, Azure will be used to host a virtual machine and domain controller that will also serve as a DNS server all under the same virtual network. In order for the domain controller to be used as a DNS server, the NIC settings will be updated to keep our DC's private IP static. The private IP address will be used as our DNS server so these settings must be applied to the 'client' VM. We then verify these updates, making sure connectivity is established and our DNS settings are as intended.
</p>

![configuring nic](https://github.com/user-attachments/assets/b8cd3a48-e7fd-4178-b186-df0916463a7e)
![setting dns server ](https://github.com/user-attachments/assets/ae8c6a39-05a9-49b8-beb3-b115e83ac097)
![ping dc1](https://github.com/user-attachments/assets/e7bc2d9c-653c-4e0a-b7c0-f5c31d1cf7cc)
![verify dns server](https://github.com/user-attachments/assets/314835c7-01ad-459d-94fe-aff6cf4e59d6)

<p>
Active Directory can now be installed and our DC-1 can now be promoted as Domain Controller, setting up a new forest (mydomain.com). Organizational units (_EMPLOYEES, _ADMINS) and a Domain Admin are created. On our 'client' VM, we add it to the Domain.
</p>

![installing ad](https://github.com/user-attachments/assets/5c8a850c-9124-4971-b712-ea1b11a116cb)
![mydomain com](https://github.com/user-attachments/assets/1eacd0c2-b809-439f-bc5d-679168ae6bd3)
![creating org unit](https://github.com/user-attachments/assets/b680b224-8bae-4ca8-8723-3adc66fc93f1)
![set domain admin](https://github.com/user-attachments/assets/0929632f-006b-4103-9e90-3c30733f6682)
![welcome 2 domain](https://github.com/user-attachments/assets/0c3db361-f514-4605-baea-935a20984f00)


<p>
To test AD features, we automate user creation using a Powershell script.
</p>

![creating users](https://github.com/user-attachments/assets/deafdfb8-fdd6-4930-968b-0543170e793d)

<p>
We update our Group policies in regards to login attempts, and create mock files to administer file permissions. We test the Account lockout policy and file permissions.
</p>

![grouppolicy edit](https://github.com/user-attachments/assets/2a228c91-656a-4b76-85da-e5b4b858921c)
![locked out](https://github.com/user-attachments/assets/ea0b2383-37ff-43b4-94ae-01c7d061e316)
![unlock acccount](https://github.com/user-attachments/assets/659ac44a-ce4e-4529-bc02-5240098c88e6)
![setting sharing](https://github.com/user-attachments/assets/7efba870-30dc-47cd-8834-66d4f88cc06f)
![access denied](https://github.com/user-attachments/assets/7a196b96-4615-4e56-b208-d02e23f71f5b)



