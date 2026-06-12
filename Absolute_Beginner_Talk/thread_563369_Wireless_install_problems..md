---
title: "Wireless install problems."
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by KLoWnTaZ on 2007-09-29
I need to know what I am doing wrong. I followin the directions here [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Here is what happens.
klown@klown-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:09.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
02:0a.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
02:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
02:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
02:0c.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
klown@klown-desktop:~$ lspci -n
00:00.0 0600: 8086:1a30 (rev 04)
00:01.0 0604: 8086:1a31 (rev 04)
00:1e.0 0604: 8086:244e (rev 05)
00:1f.0 0601: 8086:2440 (rev 05)
00:1f.1 0101: 8086:244b (rev 05)
00:1f.2 0c03: 8086:2442 (rev 05)
00:1f.3 0c05: 8086:2443 (rev 05)
00:1f.4 0c03: 8086:2444 (rev 05)
01:00.0 0300: 10de:0110 (rev b2)
02:09.0 0200: 8086:1229 (rev 08)
02:0a.0 0780: 14f1:2013 (rev 01)
02:0b.0 0401: 1102:0002 (rev 0a)
02:0b.1 0980: 1102:7002 (rev 0a)
02:0c.0 0280: 14e4:4318 (rev 02)
klown@klown-desktop:~$ sudo ndiswrapper -i ~/home/klown/Desktop/WMP54GS.inf
Password:
installing wmp54gs ...
couldn't open /home/klown/home/klown/Desktop/WMP54GS.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.
klown@klown-desktop:~$ ndiswrapper -l
lsbcmnds : invalid driver!
wmp54gs : invalid driver!


Help..

---

### Post by anewguy on 2007-09-30
Please see the beginning section of this how-to - it will get you wireless working!:)

[http://ubuntuforums.org/showthread.php?t=507505&highlight=gateway+mx3215+how+to]("http://ubuntuforums.org/showthread.php?t=507505&highlight=gateway+mx3215+how+to")

---

### Post by handydan918 on 2007-09-30
> 02:0c.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
Yup. Follow the above post. You have installed the wrong windows driver.( I have this chip in my lappy, and it's working now, but it never would without ndiswrapper!)

---

### Post by Count Doofus on 2007-10-21
Type the driver name in the CORRecT.Case !!!!!!! 

had the same problem with my Marvell card. Looked for every kind of solution that concerned hardware interface on the PCI bus.

The Real Problem was every time I issued the 
blablabla:~$ sudo ndiswrapper -i mrv8000c.inf 
I got - No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174

Until I typed the filename with the correct CASE - Mrv8000c.INF - 

GRRRRRRRRR!%@$#$###!$!@@!$@!@#!

---

