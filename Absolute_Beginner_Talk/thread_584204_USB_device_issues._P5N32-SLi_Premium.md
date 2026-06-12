---
title: "USB device issues. P5N32-SLi Premium"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by adamje42 on 2007-10-20
I'm running Ubuntu 7.10 on a P5N32-SLi Premium motherboard and shortly after login none of my USB devices send or receive any signal. They are all still receiving power but they're pretty much useless. My USB headset, and my USB generic dell optical mouse can't be used at all after about 30-120 seconds of logging in. Any help is appreciated.

---

### Post by adamje42 on 2007-10-21
[FONT="Times New Roman"]I Figure it's a problem with the USB controller. Here's the output of[/FONT] [FONT="System"]lspci[/FONT]

[FONT="System"]00:00.0 Host bridge: nVidia Corporation Unknown device 0071 (rev c1)
00:00.1 RAM memory: nVidia Corporation Unknown device 007f (rev a1)
00:00.2 RAM memory: nVidia Corporation Unknown device 0075 (rev a1)
00:00.3 RAM memory: nVidia Corporation Unknown device 006f (rev a1)
00:00.4 RAM memory: nVidia Corporation Unknown device 00b4 (rev a1)
00:01.0 RAM memory: nVidia Corporation Unknown device 0076 (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 0078 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0079 (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 007a (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 007b (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 007c (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 007d (rev a1)
00:02.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:05.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
02:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
03:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)[/FONT]

---

