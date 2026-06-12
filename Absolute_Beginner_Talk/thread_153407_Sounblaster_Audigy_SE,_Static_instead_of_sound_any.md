---
title: "Sounblaster Audigy SE, Static instead of sound? any ideas?"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by gordong11 on 2006-03-31
Hi I have installed a PCI Audigy Se card, recognized by Ubuntu as Audigy LS. IT fullt sees the card, but plays all sound static. When there is no so playing , silence as there should be, but put in a CD or Start-up sounds come through as static only. Any ideas?

admin@ubuntu:~$ lspci
0000:00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
0000:00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
0000:00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
0000:00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
0000:00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
0000:00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
0000:00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
0000:00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
0000:00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
0000:00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
0000:00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
0000:00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control[B]
0000:01:07.0 Multimedia audio controller: Creative Labs SB Audigy LS[/B]
0000:01:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

PLZ let me know if you need any other info! Thanks for help!

---

### Post by trent dillman on 2006-03-31
I remember having this problem on a friend's win box. It was set to use digital audio only.

---

