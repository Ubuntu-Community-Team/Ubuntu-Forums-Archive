---
title: "8th Failed Attempt At Ubuntu."
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by saynefox on 2007-07-20
Hello good people! I'm posting this in hopes that perhaps maybe someone will be able to help me convert this PC or help assist me into building a PC around Ubuntu. The specs I have now are as follows:

[System Summary]

System Type	X86-based PC	
Processor	x86 Family 15 Model 2 Stepping 5 GenuineIntel ~2405 Mhz	
Processor	x86 Family 15 Model 2 Stepping 5 GenuineIntel ~2405 Mhz	
BIOS Version/Date	American Megatrends Inc. 080009, 11/6/2003	
SMBIOS Version	2.3
Boot Device	\Device\HarddiskVolume1	
Hardware Abstraction Layer	Version = "5.1.2600.2180 (xpsp_sp2_rtm.040803-2158)"	
Total Physical Memory	1,024.00 MB	
Available Physical Memory	508.45 MB	
Total Virtual Memory	2.00 GB	
Available Virtual Memory	1.96 GB	
Page File Space	2.40 GB	

Item	Value	
Name	NVIDIA GeForce 6800 GT	
PNP Device ID	PCI\VEN_10DE&DEV_0045&SUBSYS_31401458&REV_A1\4&38B71F77&0&0008	
Adapter Type	GeForce 6800 GT, NVIDIA compatible	
Adapter Description	NVIDIA GeForce 6800 GT	
Adapter RAM	256.00 MB (268,435,456 bytes)	
Installed Drivers	nv4_disp.dll	
Driver Version	6.14.10.9381	
INF File	oem39.inf (nv4_NV3x section)

Audio Card: Envy24 Family Audio Controller WDM

Wireless Card Driver:

Name	[00000010] Instant Wireless PCI Card V2.7	
Adapter Type	Ethernet 802.3	
Product Type	Instant Wireless PCI Card V2.7	
Installed	Yes	
PNP Device ID	PCI\VEN_14E4&DEV_4301&SUBSYS_43011737&REV_02\4&2E98101C&0&48F0	
Last Reset	7/19/2007 12:49 PM	
Index	10	
Service Name	WMP11V27	
IP Address	192.168.1.4	
IP Subnet	255.255.255.0	
Default IP Gateway	192.168.1.1	
DHCP Enabled	No	
DHCP Server	Not Available	
DHCP Lease Expires	Not Available	
DHCP Lease Obtained	Not Available	
MAC Address	00:06:25:1D:30:9A	
Memory Address	0xFEAFE000-0xFEAFFFFF	
IRQ Channel	IRQ 21	
Driver	c:\windows\system32\drivers\wmp11v27.sys (3.8.28.0, 167.75 KB (171,776 bytes), 2/14/2007 5:51 PM)





Now I only listed some of my devices that currently have no driver support whatsoever. I could not get ndiswrapper to work either. I Do 3d modelling in Maya, which I could not get to run on linux either. I have a Wacom Stylus tablet which would not function as well. Ununtu looks fantastic and seems to have limitless potential which saddens me to think I cannot function on this OS currently given the situation. I had tried on several many occasions to get the system to run fully functional. But always winding up having to reinstall windows XP in defeat. If anyone has any insite on how to get my system up and fully functional. Or should I just build a new PC with parts easily recognizable for Ununtu? Thank you in advance.

---

### Post by ubanchaos on 2007-07-20
what ubuntu ru running on....i wanna help u so post quickly

---

### Post by wolfen69 on 2007-07-20
i know some people may disagree with me, but the perfect linux machine is built with technology that is 1 and a half to 2 years old. it gives time to developers to reverse engineer, find drivers, etc. i have tested a number of machines. linux has to fight for what it gets. don't be afraid to buy "older" stuff. you have a much better chance of compatibility. besides, linux doesnt need the latest and greatist to kick ***.

---

### Post by ubanchaos on 2007-07-20
true most old computer run linux well but if u make the computer with linux compatible parts it will be better just look for the hardware that works good with linux and u should be good because my friend just built a up to date computer and it works fine

---

### Post by spur on 2007-07-20
With what you've got grab a mag with a 'live cd' and run it. All you do is insert it into your cd drive and boot. If it runs fine you will know ubuntu will work. If it doesn't all is not lost as an 'alternative install' cd downloaded may do the trick.
With specific queries about specific problems we can be much more helpfull.

---

### Post by saynefox on 2007-07-20
Fellas, Ubuntu works. Its just that None of my componets, Like sound and Wireless Internet including my graphics card wil function. I cannot install the drivers which is definatly a problem since I do 2D and 3D graphics.

As for my system its about 3-4 years old already. Intel Processor 2.4 gighertz

---

### Post by AJB2K3 on 2007-07-20
Have you tryed the 6.06LTS version?
I had to install that on 2 machine because 7.04 just doesn't cooperate.

---

### Post by spur on 2007-07-20
so specific problems are?
Exactly what do you mean your graphics card won't work? If you say ubuntu works I presume you have a gui so it must be working to some degree.
With your nvidia card if you search these forums you will find lots of references to help you get it going optimally. In case you have tried those things let us know what you tried and what the results where. Then we have a chance to suggest something productive.

---

### Post by saynefox on 2007-07-20
My graphics card was running at a poor resolution when I had tried. When I looked for the drivers they were not working. As for internet, I have a wireless lan card which I couldn't not get to work for the life of me. Linksys 2.7 B Signal which I heart alot of dread about.

---

### Post by splintercellguy on 2007-07-20
What wireless LAN card? Can you post the output of the lspci command? A lot of these probs can be fixed :).

---

### Post by saynefox on 2007-07-20
I'm not running linux at the moment, I'm just wondering if I should give it another try with this machine. Or just build one that could run linux.


My card is a wireless PCI Linksys card I'm not sure what other specs are on it 

Name	[00000010] Instant Wireless PCI Card V2.7	
Adapter Type	Ethernet 802.3	
Product Type	Instant Wireless PCI Card V2.7	
Installed	Yes	
PNP Device ID	PCI\VEN_14E4&DEV_4301&SUBSYS_43011737&REV_02\4&2E98101C&0&48F0	
Last Reset	7/19/2007 12:49 PM	
Index	10	
Service Name	WMP11V27	
IP Address	192.168.1.4	
IP Subnet	255.255.255.0	
Default IP Gateway	192.168.1.1	
DHCP Enabled	No	
DHCP Server	Not Available	
DHCP Lease Expires	Not Available	
DHCP Lease Obtained	Not Available	
MAC Address	00:06:25:1D:30:9A	
Memory Address	0xFEAFE000-0xFEAFFFFF	
IRQ Channel	IRQ 21	
Driver	c:\windows\system32\drivers\wmp11v27.sys (3.8.28.0, 167.75 KB (171,776 bytes), 2/14/2007 5:51 PM)

---

### Post by saynefox on 2007-07-20
OH almost forgot, the last Ubuntu I tried was the one right before Fiesty faun.

---

### Post by mlentink on 2007-07-20
I don't want to sound obnoxious with this in any way, but..
It seems you have a working system in Windows. What do you hope to achieve by switching to Linux, Ubuntu?
Obviously you have tried a number of times, so you've put a lot of effort in it. What makes you want to switch?

---

### Post by HermanAB on 2007-07-20
Try different distributions till you find one that works with most things.  I suggest trying Mandriva, Suse and Fedora in addition to your Ubuntu efforts.

---

### Post by saynefox on 2007-07-20
Definatly a good point. I was hoping to mess around in a linux enviornment for a while but it just doesn't seem like its for my personal needs anyhow. I was told to switch to Mac a number of times, but that came to a matter of money which I don't have at the moment. Wasn't actually hoping to acomplish much in Linux other then just having another computer with another OS. Thank you all for your time though in at least posting back. I need sleep. Many thanks.

---

