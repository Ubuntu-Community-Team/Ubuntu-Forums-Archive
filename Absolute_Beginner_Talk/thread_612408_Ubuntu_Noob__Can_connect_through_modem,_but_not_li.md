---
title: "Ubuntu Noob:  Can connect through modem, but not linksys router"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Larongelo on 2007-11-13
Hey guys, just FYI I'm a total noob with Linux so please forgive me of my ignorance :)

I'm currently using Gutsy Gibbon, although I used the previous version of Ubuntu before but I'm still a noob.

Problem is that I can't connect to the internet through my linksys router (BEFSR41).  When I connect directly to my modem, I get a solid connection and everything works fine.  If I hook up the computer and my Xbox 360 to the router, then my Xbox gets a connection and will get online just fine but my laptop won't.  I even tried hooking the router up like just a basic switch by plugging in the cable line to one of the 4 ports in the back and hooking the laptop and Xbox to the other ports (bypassing the cable in port) and that doesn't work either!

Also, I've searched around on Google and even these forums for similar problems.  I found some, but after going through some steps given to other people to troubleshoot, I found that my problem doesn't appear to be the same.  I also found some commands on other threads that pulled some information you guys might need to know, so here they are...



laron@laron-laptop:~$ uname -r
2.6.22-14-generic
laron@laron-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M56P [Radeon Mobility X1600] [1002:71c5]
02:06.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
02:06.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
02:06.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
02:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]
02:06.4 Communication controller [0780]: Texas Instruments PCIxx12 GemCore based SmartCard controller [104c:803d]
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5753M Gigabit Ethernet PCI Express [14e4:16fd] (rev 21)
10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
laron@laron-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5753M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 21
       serial: 00:16:d4:07:96:5e
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full firmware=5753m-v3.56 ip=68.114.101.30 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
laron@laron-laptop:~$ 


Thanks so much in advance!

---

### Post by some_random_noob on 2007-11-13
Well, the connection works and your computer works - My guess is that it's either to do with router settings or some minor screw-up on your laptop's network settings. Sounds like you've overlooked something.

Are you trying to get a DHCP address or a static one? (Check your laptop's network settings). 

Good luck :) and remember... If you absolutely **can't fix it**, then maybe reset your router to it's default settings and try again.

---

### Post by Larongelo on 2007-11-13
DHCP I'm assuming... 

indeed, I hope I am just overlooking something but problem is that I can't find what that seems to be lol.

I hate not knowing how to troubleshoot something... I miss windows so much but unfortunately due to a long history of problems with this laptop I can no longer get Windows to run on it.  Ugh, guess I'm going to just reset the router and hope that works...

---

