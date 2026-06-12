---
title: "Getting Ubuntu up and running"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by jeremy.alford on 2007-03-11
I have just got Ubuntu installed on my laptop computer this morning.  I am having problems installing Kubuntu over it for starters.  Also, I cannot tell how to connect wirelessly to the internet.  Is there a place where it shows you the available wireless networks?  Finally, it will not play the dvd's that I try to watch.  Any help would be greatly appreciated.  Thanks in advance!

---

### Post by deadgobby on 2007-03-11
Hi,
 OK there is a way to install KDE on top of Gnome with out this fuss.
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)
 As for your wireless not working. Can you please provide what is the make and model of the card or USB card. 
The DVD issue that you need to install the restricted codecs for you to play DVD, mpeg, and Mp3 files. There is serval ways to to it. One is by manual ways
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Install Automatix
[http://www.getautomatix.com/](http://www.getautomatix.com/)
 Just to give a few ways. Yet, you can't do either with out a good net connection.

---

### Post by raja on 2007-03-11
You have to post more details of the problems for people to understand.
Why are you unable to install Kubuntu? Did you try ```
sudo aptitude install kubuntu-desktop
``` in the terminal ?
If your wireless card is recognized and working, you have to set up your wireless connection. Go to System >> Administration >> Network for that.
The most likely reason your DVDs are not playing is that you dont have the codecs for those. Automatix is an easy way to install the required multimedia codecs and some other applications. Look at [www.getautomatix.com/](www.getautomatix.com/) on how to install it.

---

### Post by jeremy.alford on 2007-03-12
Thank you for your help earlier.  In response to your question about my computer; here is the requested information.  Thanks again.

Here is a screenshot of my network screen under System Information in Windows:

Name	[00000001] SiS 900-Based PCI Fast Ethernet Adapter
Adapter Type	Not Available
Product Type	SiS 900-Based PCI Fast Ethernet Adapter
Installed	Yes
PNP Device ID	PCI\VEN_1039&DEV_0900&SUBSYS_00831025&REV_91\3&267A616A&0&20
Last Reset	3/12/2007 12:10 PM
Index	1
Service Name	SISNICXP
IP Address	Not Available
IP Subnet	Not Available
Default IP Gateway	Not Available
DHCP Enabled	Yes
DHCP Server	Not Available
DHCP Lease Expires	Not Available
DHCP Lease Obtained	Not Available
MAC Address	Not Available
Driver	c:\windows\system32\drivers\sisnicxp.sys (2.0.1039.1180 built by: WinDDK, 32.00 KB (32,768 bytes), 1/1/1980 12:00 AM)
	
Name	[00000004] Broadcom 802.11g Network Adapter
Adapter Type	Ethernet 802.3
Product Type	Broadcom 802.11g Network Adapter
Installed	Yes
PNP Device ID	PCI\VEN_14E4&DEV_4318&SUBSYS_03121468&REV_02\3&267A616A&0&58
Last Reset	3/12/2007 12:10 PM
Index	4
Service Name	BCM43XX
IP Address	0.0.0.0
IP Subnet	
Default IP Gateway	Not Available
DHCP Enabled	Yes
DHCP Server	255.255.255.255
DHCP Lease Expires	3/12/2007 1:22 PM
DHCP Lease Obtained	3/12/2007 12:22 PM
MAC Address	00:14:A4:4B:03:D2
Memory Address	0xE2000000-0xE2001FFF
IRQ Channel	IRQ 17
Driver	c:\windows\system32\drivers\bcmwl5.sys (3.100.46.0 built by: WinDDK, 360.38 KB (369,024 bytes), 1/1/1980 12:00 AM)

---

