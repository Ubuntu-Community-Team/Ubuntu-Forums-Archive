---
title: "problem with screen resolution"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by billy_eee on 2007-06-20
i have a gateway FPD2275W monitor. resolution is 1680X1050. i cannot get this resolution on my computer. i followed the instructions on this site: [http://tuxicity.wordpress.com/2006/12/02/configure-your-resolution-in-ubuntu-and-debian/](http://tuxicity.wordpress.com/2006/12/02/configure-your-resolution-in-ubuntu-and-debian/)

i restarted ubuntu but that didnt work and I still  cannot see 1680X1050 in system-->preferences-->screen resolution.
right now my screen looks weird, all the words are kinda stretched and it hurts when i look at it. how can i fix my screen? thanks

---

### Post by NeoLithium on 2007-06-20
What video card did you have inside your computer? (If you don't have the info handy, you can find out by opening up a terminal Applications -> Accessories -> Terminal) and typing in:
```
lspci
```
Just copy and paste that here and we'll help you out :)

---

### Post by billy_eee on 2007-06-20
here you go:
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Communication controller: Conexant Unknown device 2f40
01:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4353 (rev 14)
joejohn@joejohn:~$

---

### Post by NeoLithium on 2007-06-20
Assuming that you have Feisty installed, there's a walkthrough here for NVIDIA drivers that will help you get set up with the proper ones for your video card :)  [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card)

---

