---
title: "[SOLVED] Internal Wireless help with HP notebook"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by aerisismine on 2007-11-21
Hey everyone!

So, I'm completely new to linux.  After years of suffering though XP and then a short bout with Vista, it was time for change.  My friend recommended Ubuntu, so here I am.  The one thing that I'm still having a lot of trouble with is wireless internet.  I've tried setting up my wireless N external card with no luck.  Right now, I would be absolutely thrilled if someone could help me set up my internal wireless card.  I already tried a couple of things that worked for other people, but I always seem to hit a snag, and find all the code very hard to follow still.  Any assistance would be greatly appreciated!

~Kei

---

### Post by MrFSL on 2007-11-21
Welcome!

Well for starters it would help if we knew what type of wireless adapter you have.

Please open a terminal ( Applications > Accessories > Terminal) and type the following. When you are done please post the output:
```
lspci | grep -i wireless
```

---

### Post by aerisismine on 2007-11-21
hey, thanks for your prompt help ^^

When I input the code, all I get is a new command line
ethan@Ethan:~$ lspci | grep -i wireless
ethan@Ethan:~$ 

when I cut it down to lspci I get this,

 ethan@Ethan:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

Does this help you at all?

---

### Post by MrFSL on 2007-11-21
> 01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

This is what I was looking for. I guess I will start suggesting ***lspci | grep -i net***

What about the ouput of:

```
iwlist eth1 scanning
```

---

### Post by aerisismine on 2007-11-21
ethan@Ethan:~$ iwlist eth1 scanning
eth1      Interface doesn't support scanning.

---

### Post by aerisismine on 2007-11-21
I tried setting it up with a static IP and using my wireless network in non roaming mode.  Then I retried your code, and got this.

ethan@Ethan:~$ iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:1C:10:4F:CC:A8
                    ESSID:"Miller_WLAN"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=95/100  Signal level=-49 dBm  Noise level=-66 dBm
                    Extra: Last beacon: 452ms ago


If I unplug from the router, I still don't have wireless access, but my wifi light comes on.

---

### Post by aerisismine on 2007-11-22
Hey, I have a friend who helped me out, but I greatly appreciate your help!  I've got my internal wireless card working.

---

### Post by MrFSL on 2007-11-23
If you would, please post how you got it working,.... for the next guy who is having problems.

---

### Post by aerisismine on 2007-11-23
Of course!  What was I thinking?

I followed directions from this link: 

[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

---

