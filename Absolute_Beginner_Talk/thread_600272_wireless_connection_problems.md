---
title: "wireless connection problems"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by fatso on 2007-11-02
I have an acer aspire 3633 with 802.11 b/g wireless lan, and a linksys wrt54g router. How do I connect to the internet? Do I have to download a driver to the 802.11, and where do I get it?

---

### Post by Griffiss on 2007-11-02
Post the outputs to the following commands (type them in the terminal)

lspci

sudo lshw -C network

iwconfig


then someone can help you

---

### Post by fatso on 2007-11-02
> **Griffiss said:**
> Post the outputs to the following commands (type them in the terminal)

lspci

sudo lshw -C network

iwconfig


then someone can help you


lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

sudo lshw -C network
 *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:16:36:38:1d:d5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=10.0.0.2 latency=173 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth1
       version: 02
       serial: 00:16:ce:42:7f:b7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by vmsda on 2007-11-02
> **Griffiss said:**
> Post the outputs to the following commands (type them in the terminal)
lspci
sudo lshw -C network
iwconfig

then someone can help you

Even though I have the wireless hw installed on a different machine, my outputs to the commands are the same as Fatso's. So I shall be watching this thread with keen interest.

One question: since there seem to be quite a few problems with Linux and wireless hardware, where can one find the recommended hardware for a Linux installation, which would presumably yield a failsafe installation and operation?

Thanks in advance for the help.

---

### Post by SteveHoffmanUK on 2007-11-02
Have you tried this:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by Griffiss on 2007-11-02
This is a relatively old walkthrough, but it's specifically for your wireless card, and looks like it should still work:

[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)

If you have WEP or WPA encryption, have a look at this:

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

