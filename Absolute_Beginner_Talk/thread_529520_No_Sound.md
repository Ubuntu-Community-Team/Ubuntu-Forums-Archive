---
title: "No Sound"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by SteveJB on 2007-08-19
Hello, I'm a noob from Winblows. Having problems getting my on-board sound to work on this junk ASRock 939 C-Media 6501. Any help or ideas would sure be welcome. 

Here is the information in terminal:
LSPCI
steve@steve-desktop:~$ lspci
00:00.0 Host bridge: ALi Corporation M1695 K8 Northbridge [PCI Express and HyperTransport]
00:01.0 PCI bridge: ALi Corporation PCI Express Root Port
00:02.0 PCI bridge: ALi Corporation PCI Express Root Port
00:04.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:05.0 PCI bridge: ALi Corporation AGP8X Controller
00:06.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:07.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:07.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:11.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
00:12.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:13.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0295 (rev a1)
steve@steve-desktop:~$ 

And LSUSB,

steve@steve-desktop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0d8c:0201 C-Media Electronics, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 139b:0005  
Bus 001 Device 001: ID 0000:0000  
steve@steve-desktop:~$

As a note I can go to system/sounds, and select "usb" and press test, I hear the tone, but that is the only place I get any sound. If I select "auto detect" the program will close.

Thanks,
Steve

---

### Post by sailor2001 on 2007-08-19
in synaptics, check alsa base and alsa oss.......next right click sound icon upper right on panel to open volume control and then click edit/ preferences and tick what you need

---

### Post by mikeyphi on 2007-08-19
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Read through the above - it should fix/narrow the issue - then report back with more info!!

---

### Post by RomeReactor on 2007-08-19
Hi. I couldn't find much about your card, but according to [this post]("http://ubuntuforums.org/showpost.php?p=2993404&postcount=63") it's not supported by Alsa 1.0.13. The most up-to-date version [is 1.0.14]("http://www.alsa-project.org/main/index.php/Main_Page"), though [I couldn't tell]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-C-Media") if it's now supported.

---

### Post by SteveJB on 2007-08-19
Thanks all, will try the above and get back with results.

Steve

---

