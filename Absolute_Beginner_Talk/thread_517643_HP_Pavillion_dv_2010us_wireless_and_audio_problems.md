---
title: "HP Pavillion dv 2010us wireless and audio problems"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by wAcKiPaKi86 on 2007-08-04
Ok so I just installed Ubuntu 7.04 on my HP Pavillion dv2010us and I am unable to connect to my wireless network and I have no audio. I think it detects my cards but I think i need to configre something to get both of them to work

any help PLEASE!!!

\\:D/\\:D/

---

### Post by overdrank on 2007-08-04
> **wAcKiPaKi86 said:**
> Ok so I just installed Ubuntu 7.04 on my HP Pavillion dv2010us and I am unable to connect to my wireless network and I have no audio. I think it detects my cards but I think i need to configre something to get both of them to work

any help PLEASE!!!

\\:D/\\:D/

Hi and welcome could you give us some information on your hardware. You could post the output of the lspci command in the terminal located under applications, accessories, terminal and we maybe able to help better. :)

---

### Post by wAcKiPaKi86 on 2007-08-04
ok here is it

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


now i am able to connect to the internet via a cable from my router.

so i want my wireless and sound to work?
what next?

---

### Post by overdrank on 2007-08-04
Well it looks like you have work ahead of you for the wireless card
01:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card
Here is a link to some info on it
[http://ubuntuforums.org/showthread.php?t=515398&highlight=Dell+Wireless+1390+WLAN+Mini-PCI+Card](http://ubuntuforums.org/showthread.php?t=515398&highlight=Dell+Wireless+1390+WLAN+Mini-PCI+Card)
And for your sound issues you may find help on this thread 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Hope this helps and good luck! :popcorn:

---

