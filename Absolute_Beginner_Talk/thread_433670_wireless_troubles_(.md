---
title: "wireless troubles :("
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Disc00rd on 2007-05-05
Hi, yeah i'm brand spanking new to Ubuntu, well more a less new to linux. And after getting my brand new laptop a month ago i have been left with the bitter taste that is Vista! OMG don't get me started. Okay so i went to ubuntu.org and got 7.04. the install went great until it came time to connect to the net :/ okay so i am pure n00b but i know for sure that my wireless isn't working :) if i could get some help it would be much appreciated.

Okay so from looking all over the net and seeing what other people had to do to get help this is my computer and the results i got from typing in lspci, sudo lshm -C network, iwconfig. lsusb and uname -r just to help you guys help me.

oh this is a Acer Aspire 3053WXMI using an AMD Sempron processor 3400+ with an 802.11 b/g wireless LAN

Righto for lspci
```

disc00rd@disc00rdia:~$ lspci 
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10) 
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37 
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80) 
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) 
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) 
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) 
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83) 
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) 
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01) 
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80) 
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M] 
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10) 
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01) 
08:01.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) 
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01) 
08:01.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01) 
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
08:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01) 

```

For sudo lshw -C network
```
disc00rd@disc00rdia:~$ sudo lshw -C network 
Password: 
  *-network:0              
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 2 
       bus info: pci@08:02.0 
       logical name: eth0 
       version: 10 
       serial: 00:16:36:b5:92:18 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s 
       resources: ioport:a000-a0ff iomemory:d0211c00-d0211cff irq:21 
  *-network:1 UNCLAIMED 
       description: Ethernet controller 
       product: AR5005G 802.11abg NIC 
       vendor: Atheros Communications, Inc. 
       physical id: 4 
       bus info: pci@08:04.0 
       version: 01 
       width: 32 bits 
       clock: 33MHz 
       capabilities: cap_list 
       configuration: latency=168 maxlatency=28 mingnt=10 
       resources: iomemory:d0200000-d020ffff irq:20 
```


For iwconfig i got
```
disc00rd@disc00rdia:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 

```

For lsusb i got
```
disc00rd@disc00rdia:~$ lsusb 
Bus 003 Device 001: ID 0000:0000   
Bus 002 Device 001: ID 0000:0000   
Bus 001 Device 003: ID 15ca:00c3   
Bus 001 Device 001: ID 0000:0000   
```

and last of all for uname -r i got
```
disc00rd@disc00rdia:~$ uname -r 
2.6.20-15-generic 
disc00rd@disc00rdia:~$  

```

Okay thanks guys i hope you can help me out!

---

### Post by mikeyphi on 2007-05-05
What (if anything) shows under - System - Administration - Network? 
If it's there, select and enable.

If you've already done all this - sorry, but first things first!

---

### Post by Disc00rd on 2007-05-05
Yeah it only shows wired connection with address :dhcp and modem connection which isn't configured yet

---

### Post by Teamgeist on 2007-05-05
Have you installed the package linux-restricted-modules-generic?
If not do so by typing ```
sudo apt-get install linux-restricted-modules-generic
``` in a terminal.
Restart your computer and let us know if it worked.

---

### Post by Disc00rd on 2007-05-05
okay typed it in and got this

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-restricted-modules-generis is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

the restarted and got nothing still

---

### Post by mikeyphi on 2007-05-05
So - the hardware is at least listed but has a problem!
I suggest you work your way through this guide and come back here with any problem areas: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

(assuming you haven't already!!)

---

### Post by EduMaxwell on 2007-05-09
I seem to have the same problem, except that my wireless device was working perfectly fine in Feisty until several days ago.  The problem turned up after I had tried to connect to our wireless network at school (unsuccessfully on an open network).  I returned home and suddenly NetworkManager no longer showed my wireless -- nor did System>Administration>Network.

My terminal readouts are almost exactly the same (*-network:1 UNCLAIMED), and my card is a AR5005G.  It seems to be a simple matter of reloading the drivers, since my card was working with Feisty until recently, but alas I have forgotten how to do even that.

I was hoping this thread would continue to reveal new ideas.  If anything, I would like to be directed to explicit instructions on how newbies should load supported drivers (from resource CD or otherwise).

Thanks!

PS I began working through the Wireless troubleshooting guide until I realized that it might have to do with an corrupted driver.

---

### Post by ugm6hr on 2007-05-14
My Acer Aspire 5051 has an Atheros5005 wifi card too.  From a fresh Xubuntu7.04 install, it works if you activate the "Restricted Driver" - in Xubuntu:
1. Applications -> System -> Restricted Drivers Manager
2. Enter administrator password where requested
3. "Atheros Hardware Access Layer" should be enabled.  If it's not there - try getting it from Synaptic Package Manager (sorry - not sure what it will be listed as - my Xubuntu autodetected it).

Hope that's helpful.  I use Network Manager to connect to my WPA network.

---

