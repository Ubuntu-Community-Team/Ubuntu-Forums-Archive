---
title: "Help me select my wireless driver: I have 4 options, and I cannot tell the differance"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Squish on 2008-02-25
Hi - I have been trying to get the following card to work on my desktop, and if I cannot get it working soon, I will be forced by my landlord (weird pointless story) to go back to windows

So first off, here is my card
[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1122062238277&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3827739789B01]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1122062238277&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3827739789B01") Technically the card is the wmp54gx4, not the wmp54gx, however there is more documentation on the gx than the gx4.

Anyways, to my understanding, I have 2 ways of going about this card to get it to work.
Linux Native Drivers:
[http://linux-wless.passys.nl/query_part.php?brandname=Linksys]("http://linux-wless.passys.nl/query_part.php?brandname=Linksys")
802.11g 	 WMP54G 	 man: 14e4 dev: 0013 	 PCI 	 Broadcom 	 bcm43xx 	 yellow  	 [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)
802.11g 	WMP54G v. 3 	man: 14e4 dev: 4320 	PCI 	Broadcom 	Bcm43xx 	green 	[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)
802.11g 	WMP54G v.4 	man:1814 dev:0201 	PCI 	Ralink 	rt2x00 	green 	Driver available from manufacturer: [http://web.ralinktech.com/ralink/Home/Support/Linux.html](http://web.ralinktech.com/ralink/Home/Support/Linux.html) , or [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
802.11g 	WMP54G v. 4.1 	dev: 0055 	PCI 	Ralink 	RT61 	green 	Driver available from manufacturer: [http://web.ralinktech.com/ralink/Home/Support/Linux.html](http://web.ralinktech.com/ralink/Home/Support/Linux.html) , or [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)

4 differant drivers, but I have not a clue which one is appropriate; Please help me find out.


Windows Drivers - NTFS
I have only found one driver, and it is the same for both the cards. I however do not know what to do with the driver I download ([http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1169671167871&packedargs=sku%3DWMP54GX4&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=6787167871B01&displaypage=download]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1169671167871&packedargs=sku%3DWMP54GX4&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=6787167871B01&displaypage=download")) I was wondering what file I should load for the wireless manager.

Thank you ~ Please please please... work...

---

### Post by Het Irv on 2008-02-25
In the terminal type 
```
lspci
```

post the results here and I should be able to give you a good answer

---

### Post by Squish on 2008-02-25
One thing I should mention about the device, is that it is kinda weird. It works, because I have used it in windows, however during the install process, you actually have to install the driver first before plugging in the card, otherwise it will not work.


00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:09.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Ethernet controller: Airgo Networks Inc AGN300 802.11 a/b/g True MIMO Wireless Card (rev 01)
01:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
06:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
06:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
07:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)

---

### Post by Het Irv on 2008-02-26
```
01:07.0 Ethernet controller: Airgo Networks Inc AGN300 802.11 a/b/g True MIMO Wireless Card (rev 01)
```

There is your wireless card, the bad thing is I am not sure which to tell you to use (I was hoping that this line would have broadcom or ralink in it.  Try downloading the windows drivers and use NDISWrapper to get it to work.

---

### Post by Squish on 2008-02-26
hmmm, I think this is actually on board my motherboard, which means that my computer is not detecting it. currently it is working under windows, so maybe I will try it again

---

### Post by Het Irv on 2008-02-26
Your motherboard has built-in wireless?  I would suggest a dual boot if you cannot get the wireless to work,  this will give you more time to play around with Ubuntu while still having an internet connection.

---

### Post by Squish on 2008-02-27
Thats what I did ~ Bleck

Well at least I can now play games...

---

