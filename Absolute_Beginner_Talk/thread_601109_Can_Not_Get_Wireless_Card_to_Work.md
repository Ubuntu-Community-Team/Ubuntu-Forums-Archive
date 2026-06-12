---
title: "Can Not Get Wireless Card to Work"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by cknightfl on 2007-11-02
Hey, 

I can not get my wireless card install on ubuntu.  I just upgrading to 7.1.  I have a hp dv9205us.  I can not find the model of the wireless card.  It is the one that came with the laptop if that helps anyone.  What do I need to do to install it.

Thanks In Advance,
cknightfl

---

### Post by overdrank on 2007-11-02
> **cknightfl said:**
> Hey, 

I can not get my wireless card install on ubuntu.  I just upgrading to 7.1.  I have a hp dv9205us.  I can not find the model of the wireless card.  It is the one that came with the laptop if that helps anyone.  What do I need to do to install it.

Thanks In Advance,
cknightfl

Hi and you can find the model of the wireless card with this command ```
lspci
``` 
In the terminal, located under applications, accessories, terminal. And then you can search the forums for help or post back here. :KS

---

### Post by cknightfl on 2007-11-02
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
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

That is what it said when i ran that command 
Im assuming it is the 
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

Where do I go from here

Thanks Again

---

### Post by overdrank on 2007-11-02
This may help
[http://ubuntuforums.org/search.php?searchid=30478670](http://ubuntuforums.org/search.php?searchid=30478670)
There are a couple of "how to" and you can choose what is best for you. I have not used that card so Good luck! :KS

---

### Post by mdpalow on 2007-11-03
when you install 7.10 it should automatically install drivers for Broadcom. Are you connected to the Internet (cable/CAT5) when you install 7.10? You should be connected by cable when installing 7.10, so it can get downloads from Internet.

Try install again with cable connection. Wireless light should come on after install.

Good luck...

---

