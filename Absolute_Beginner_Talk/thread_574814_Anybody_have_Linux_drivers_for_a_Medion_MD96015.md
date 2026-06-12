---
title: "Anybody have Linux drivers for a Medion MD96015???"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by paul6888 on 2007-10-13
I can't find any drivers at all for this thing, especially the wireless..... Anyone here have them?

---

### Post by overdrank on 2007-10-13
> **paul6888 said:**
> I can't find any drivers at all for this thing, especially the wireless..... Anyone here have them?

Hi and welcome, please post the output of the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware and we may be able to help.

---

### Post by paul6888 on 2007-10-13
ubuntu@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
06:09.0 Ethernet controller: Winbond Electronics Corp W89C33D 802.11 a/b/g BB/MAC



Pretty obvious that I have a nVidia nForce motherboard.

---

### Post by Martje_001 on 2007-10-13
All drivers (except for wireless) are automatically installed. Can you tell us what's not working?

---

### Post by paul6888 on 2007-10-13
The wireless, of course.

---

### Post by overdrank on 2007-10-13
> **paul6888 said:**
> The wireless, of course.
HI and it appears that the card 
06:09.0 Ethernet controller: Winbond Electronics Corp W89C33D 802.11 a/b/g BB/MAC
Is not well supported by linux.
[http://ubuntuforums.org/search.php?searchid=28735631](http://ubuntuforums.org/search.php?searchid=28735631)

:(

---

### Post by paul6888 on 2007-10-13
I'm trying ndiswrapper, then. I should probably mention I'm using the Live CD.

---

