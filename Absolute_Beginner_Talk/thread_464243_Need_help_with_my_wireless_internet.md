---
title: "Need help with my wireless internet"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Rensole on 2007-06-04
hey im very new to the ubuntu group and just installed it onto my HP pavilion dv6225us entertainment notebook pc, so far so good and the installation was a cakewalk until the wireless internet. i skipped to complete the installation, but now that its running fine I'd like to fix my wireless internet problem. 

I have a Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card in it so i just need some directions as to get the wireless up and running on it, thanks for any help you can give me and all the help you've already given me;)

---

### Post by kevdog on 2007-06-04
Can you list both the contents of:

lspci

and 
lspci -n

What type of drivers do you have for the card??? Linux drivers or Windows XP or Vista drivers??

---

### Post by ncappel1 on 2007-06-04
Is your card listed here? 
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)

this is from the wifidocs in the wiki: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by Rensole on 2007-06-04
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
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by Rensole on 2007-06-04
and lspci -n

00:00.0 0500: 10de:02f0 (rev a2)
00:00.1 0500: 10de:02fa (rev a2)
00:00.2 0500: 10de:02fe (rev a2)
00:00.3 0500: 10de:02f8 (rev a2)
00:00.4 0500: 10de:02f9 (rev a2)
00:00.5 0500: 10de:02ff (rev a2)
00:00.6 0500: 10de:027f (rev a2)
00:00.7 0500: 10de:027e (rev a2)
00:02.0 0604: 10de:02fc (rev a1)
00:03.0 0604: 10de:02fd (rev a1)
00:05.0 0300: 10de:0244 (rev a2)
00:09.0 0500: 10de:0270 (rev a2)
00:0a.0 0601: 10de:0260 (rev a3)
00:0a.1 0c05: 10de:0264 (rev a3)
00:0a.3 0b40: 10de:0271 (rev a3)
00:0b.0 0c03: 10de:026d (rev a3)
00:0b.1 0c03: 10de:026e (rev a3)
00:0d.0 0101: 10de:0265 (rev f1)
00:0e.0 0101: 10de:0266 (rev f1)
00:10.0 0604: 10de:026f (rev a2)
00:10.1 0403: 10de:026c (rev a2)
00:14.0 0680: 10de:0269 (rev a3)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
03:00.0 0280: 14e4:4311 (rev 01)
07:05.0 0c00: 1180:0832
07:05.1 0805: 1180:0822 (rev 19)
07:05.2 0880: 1180:0843 (rev 01)
07:05.3 0880: 1180:0592 (rev 0a)
07:05.4 0880: 1180:0852 (rev 05)

as for ht

---

### Post by kevdog on 2007-06-04
Here's a thread that addresses exactly what you want.  I havent read through the whole thread, its over 50 pages long.  

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

Just my opinion

Generally there are 3 ways to get your wireless card working
1. Wireless card that comes specifically with linux drivers (yours does not -- most do not!)
2. Ndiswrapper
3. bcm43xx cutter

Ive used both approach 3 and 2.  Im not sure what the entire post suggests, but #3 is a lot easier to set up than #2.  The only downside to #3 -- which no one tells you about -- is that the card only runs at maximum 11 MB/s -- which is equivalent to 802.11b rather than at maximum 54 Mb/s -- equivalent of 802.11g.  If anyone in the post states the bcm43xx cutter approach works, I would get that up and running.  Its very easy.  The broadcom approach although it works great, is very tempermental in the setup so be forewarned.

---

### Post by Bohlio on 2007-06-04
I think you may need Ndiswrapper for all broadcom cards, but I may be wrong about that. I have a Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller and it sucked big time to set up.

---

