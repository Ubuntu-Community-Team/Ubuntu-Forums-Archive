---
title: "Very slow/no wireless.."
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Veoeluz on 2008-02-21
Ok, first off, thank you! :D  This is my laptop connecting to my school's wireless internet, which I have no trouble at all connecting to when I boot into windows, but when I try to connect to wireless with gutsy, I get a very slow, or no connection at all.  It recognizes there are networks available and tries to connect.  

I have enabled the restricted drivers, and I'm pretty sure that I have everything up to date.  I have also followed the instructions on this page , but to no avail...[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4")

Any ideas?  Thanks :D

lspci and lshw -C network are below

```
^[[Asteve@steve-laptoplspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
08:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
08:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
08:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
steve@steve-laptop:~$ sudo lshw -C network
[sudo] password for steve:
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:03:25:35:51:09
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=10.4.3.105 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:08:07.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:5c:d3:c2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
steve@steve-laptop:~$ 

```

---

### Post by luisromangz on 2008-02-21
You have a broadcom card using the bcm43xx driver, you should try ndiswrapper. I also had a slow connection which suffered from random interruptions while using bcm43xx, but ndiswrapper works perfectly.

---

### Post by Crafty Kisses on 2008-02-21
> **luisromangz said:**
> You have a broadcom card using the bcm43xx driver, you should try ndiswrapper. I also had a slow connection which suffered from random interruptions while using bcm43xx, but ndiswrapper works perfectly.

The NDISwrapper would probably be best for you, try it.

---

### Post by spiderbatdad on 2008-02-21
you might try disabling ipv6 via /etc/modprobe.d/aliases
to look like this: ```
alias net-pf-9  x25
alias ipv6 off
alias net-pf-10 ipv6 off
alias net-pf-11 rose
alias net-pf-12 decnet
# 13 NETBEUI
```

---

### Post by Veoeluz on 2008-02-21
I tried a few of the guides to install ndiswrapper (i did remember to disable the restricted drivers), but they didn't seem very clear.  I tried one of the automated version (used python or something).. does anyone have a link to a tried and true method?

Thanks for your help!

---

### Post by Dr. Octagon on 2008-02-21
You might look here

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

