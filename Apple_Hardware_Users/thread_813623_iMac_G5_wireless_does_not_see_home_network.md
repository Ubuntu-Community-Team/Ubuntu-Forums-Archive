---
title: "iMac G5 wireless does not see home network"
date: 2008-05-31
forum: Apple Hardware Users
---

### Post by garbageguts on 2008-05-31
Hi folks,

I have Ubuntu Hardy running on an iMac G5 and am currently having a ball learning how it all works.

Unfortunately I cannot figure out how to get the wireless working properly (our home network and internet access is wireless only).

I have a temporary set up where the iMac shares the wireless internet connection from my mums iBook (running Tiger) which is connected via an ethernet cable (Ubuntu sees it as a normal network connection), but obviously this is not ideal (she wants her iBook back!)

Hardware Drivers told me I needed special firmware for my card (an Airport Extreme) called "Broadcom B43 wireless driver" which it downloaded and installed for me, but I still cannot connect to my home wireless network (nothing shows up in the Network Manager) even after a restart.

Forum search has failed me (there are many topics about wireless, but nothing for my problem that I could see), can anyone point me in the right direction?

Many thanks.

btw, here's my "lspci" incase it is useful:
```
0000:f0:0b.0 Host bridge: Apple Computer Inc. U3L AGP Bridge
0000:f0:10.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
0001:00:01.0 PCI bridge: Apple Computer Inc. Shasta PCI Bridge
0001:00:02.0 PCI bridge: Apple Computer Inc. Shasta PCI Bridge
0001:00:03.0 PCI bridge: Apple Computer Inc. Shasta PCI Bridge
0001:01:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0001:01:07.0 Class ff00: Apple Computer Inc. Shasta Mac I/O
0001:01:0b.0 USB Controller: NEC Corporation USB (rev 43)
0001:01:0b.1 USB Controller: NEC Corporation USB (rev 43)
0001:01:0b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0001:02:0c.0 IDE interface: Broadcom K2 SATA
0001:02:0d.0 Class ff00: Apple Computer Inc. Shasta IDE
0001:02:0e.0 FireWire (IEEE 1394): Apple Computer Inc. Shasta Firewire
0001:03:0f.0 Ethernet controller: Apple Computer Inc. Shasta (Sun GEM)
```

---

### Post by stueng on 2008-05-31
Give the output of iwconfig and paste it here

your alternative to using native Linux drivers is to ndiswrapper if you like; you can follow my instructions substituting the correct windows drivers (as my instructions are for the BCM4328) at [http://www.lostpeg.co.uk/content/view/34/76/]("http://www.lostpeg.co.uk/content/view/34/76/")

Where possible its better to use native Linux drivers but perhaps while you troubleshoot the connection you would like to use ndiswrapper to at least get a connection

Stu

---

