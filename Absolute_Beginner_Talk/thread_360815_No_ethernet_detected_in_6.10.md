---
title: "No ethernet detected in 6.10"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by HgBoy on 2007-02-13
I have disabled the IFVB6 or whatever in firefox, have typed in the ifconfig, and it show no eth0. I have checked my /etc/network/config files and the show all of the auto eth0, eth1, etc... I have an ASRock motherboard with NVIDIA NF 6100-430 chipset, and a Gigabit LAN 10/100/1000 MB/s, and Giga PHY Realtek RTL8211B. I have only been using edgy for about 48 hours now and have had absolutely no experience with Linux before. This all seems overwhelming right now, and having the internet working properly is something that I must have soon. 

(motorola sb5101 surfboard cable modem and time warner cable internet)

Physical Address: 00-03-25-12-04-43
IP Address: ***
Subnet Mask: 255.255.224.0
Default Gateway: ***
DHCP Server: ***
Lease Obtained: 2/13/2007 3:47:54 PM
Lease Expires: 2/14/2007 7:15:40 AM
DNS Servers: 65.24.7.3, 65.24.7.6

I don't know where to start with all of this information.

---

### Post by Jabran Asghar on 2007-02-13
Have you tried

$sudo lshw | grep "eth"

This  should display any ethernet cards detected in your system. If you see ethX, and ethX is not in /etc/network/interfaces files, then add it and try

$sudo /etc/init.d/networking restart

Then use "ifconfig" to check again.

You can also try following command to see in a GUI if the corresponding NIC is enabled or not.
$gksu network-admin


Hope this helps.

Jabran

---

### Post by HgBoy on 2007-02-13
when i try the first command line, the system tells me that i should try the command as "super user". I guess all I really need to know, is where to download and how to install a driver that will work for my particular ethernet driver. If the particular driver in question is written in source, I would need to know the steps to compiling it. I need to have the internet working soon, as I will be losing my laptop this weekend because I sold it to build my new PC.

---

### Post by Jabran Asghar on 2007-02-14
When you will issue a command with "**sudo** ....", system will ask you for **your**' password. If you are logged in using the username that you created during installation, then by giving your password on the password prompt will allow you to run the command(s) as super user ("Administrator" in windows terms).

The commands I mentioned earlier may help you to identify whether Ubuntu at all detected your Ethernet card or not. (Installing a driver for the **detected** NIC is the second thing). It may be that the Ethernet card is being identified as eth**X**other than eth0, eth1, etc. (this happened with me once).

In my experience I never needed to install additional drivers for Wired Network cards. But yes, for Wireless cards, you may have some trouble. If this is your case, then look for using "ndiswrapper" on these forums --> That will enable you to use your Windows driver on Linux. (Also use "iwconfig" instead of "ifconfig" in that case).

---

### Post by ihavenuthing on 2007-02-18
> **Jabran Asghar said:**
> When you will issue a command with "**sudo** ....", system will ask you for **your**' password. If you are logged in using the username that you created during installation, then by giving your password on the password prompt will allow you to run the command(s) as super user ("Administrator" in windows terms).

The commands I mentioned earlier may help you to identify whether Ubuntu at all detected your Ethernet card or not. (Installing a driver for the **detected** NIC is the second thing). It may be that the Ethernet card is being identified as eth**X**other than eth0, eth1, etc. (this happened with me once).

In my experience I never needed to install additional drivers for Wired Network cards. But yes, for Wireless cards, you may have some trouble. If this is your case, then look for using "ndiswrapper" on these forums --> That will enable you to use your Windows driver on Linux. (Also use "iwconfig" instead of "ifconfig" in that case).

if i ran the command to grep for "eth" and nothing was returned ... what should I do ? 
The ethernet is wired onto my mobo ... it was working when I first ran the live cd.... .now its not even detected in windows or in linux.

---

