---
title: "more card reader woes... compaq v3118AU MSPro Duo"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by ozPATT on 2006-12-05
hi everyone, 

I took some nice pics with my phone tonight, and sat down to try out the card reader in my laptop.

Didn't work, but that didnt surprise me as I seem to find a few things that require hunting for solutions to make them work. :) 

However, I can't seem to find a way to make my cad reader work. I have a sony ericsson w810i, with a Memory Stick Pro Duo card. (and Memory Stick Duo Adapter)

My laptop has a card reader for the following: SD, MS/Pro, MMC, XD

Please could someone tell me how I can get it to work? I have tried lspci, which gives me the following:

> 00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
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
01:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:09.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

The last ones seem to be relevant? and I also did dmesg but that brought a load of stuff up i have no idea what it means.

Any help would be appreciated. 

Many thanks

Patrick

---

### Post by bodhi.zazen on 2006-12-06
With the device attached to your computer, what happens when in a terminal you type:```
sudo fdisk -l
```

Note: That is a small "L"....

---

