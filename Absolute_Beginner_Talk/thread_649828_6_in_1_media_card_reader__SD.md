---
title: "6 in 1 media card reader / SD"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by crav on 2007-12-25
Trying to access some stuff on my built in 6-in-1 media card reader on my laptop. It worked in previous versions of Ubuntu, but seems not to now. It's an HP dv8305us.

Output from lspci:

[CODEcrav@AlphaCrav:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
**06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller**
06:04.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)[/CODE]

any help is greatly appreciated!

---

### Post by icheyne on 2007-12-25
This is a really good tutorial:

[http://www.novell.com/coolsolutions/feature/11637.html](http://www.novell.com/coolsolutions/feature/11637.html)

---

### Post by crav on 2007-12-25
Thanks, but that guide is for mounting a USB drive, what would I do for my built-in card reader (as opposed to one via USB)

---

### Post by icheyne on 2007-12-26
Sorry. :-S

---

### Post by rodrigo.galvez on 2008-04-25
There isnt a solution for thisss... I have a laptop HP DV6648se and is the same no way to mount the 5-in-1 integrated Digital Media Reader... and there isnt instructions on the web...
I install 8.04 but dont work

i Have a post with the same problem in a lot o forums and no one has a solution
[http://ubuntuforums.org/showthread.php?t=766892](http://ubuntuforums.org/showthread.php?t=766892)

---

