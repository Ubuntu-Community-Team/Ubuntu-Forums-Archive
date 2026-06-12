---
title: "dont know how to make wireless work!"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by pontifex3 on 2007-06-12
HI i have dv2000 notebook, and i have no idea of how to make the wireless internet work, in the specifications it says i have a PCI Express whatever that means, anyway when i open the Network menu, the wireless conection says it hasn't been configured yet, doest anybody know how do i get this working? thanks a lot!

---

### Post by Inxsible on 2007-06-12
What are the errors that you are getting? Tell us what you have tried.
 
If its only that you havent been able to see your network, do this. Make sure you are not on the wired network.
 
Do you see a network icon near the system clock?
Click on that icon and it will list all the available wireless networks. Select the one that is yours and enter the requisite passwords and such.

---

### Post by pontifex3 on 2007-06-14
no, the problem is that ubuntu didnt configure the wireless card by itself, there is no icon where it shows the connections, thats my problem, here are my computer specifications so you can see what card i have
```

oyuki@Keroberos:~$ lspci
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
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
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
01:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
oyuki@Keroberos:~$ 


```

---

### Post by drs305 on 2007-06-14
here is the line that is important to wireless:

```
01:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
```

As a starter, which version of ubuntu are you running? A lot of networking improvements were made in feisty. If you do a search for broadcom you might want to limit your searches to feisty wireless issues if that is the version you have installed. Searching for posts in the last 60 days would ensure you are getting the latest advice on broadcom wireless problems (of which there have been many).

One other suggestion about searches, if you find a post that recommends something, read down further and see what success the reader had by following the advice. Start wtih successes and go back and try the failures only if you are desperate for a solution. ;-)

Edited for link:
I did a search for "broadcom 1390 ubuntu" and found a very extensive howto . Note that the original post was from last year. You might want to start at the end, which is only a few days old, and read the recent posts first.

Link: 
[http://ubuntuforums.org/showthread.php?t=297092&page=7](http://ubuntuforums.org/showthread.php?t=297092&page=7)

---

