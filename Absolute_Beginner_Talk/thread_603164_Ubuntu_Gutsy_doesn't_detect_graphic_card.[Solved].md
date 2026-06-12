---
title: "Ubuntu Gutsy doesn't detect graphic card.[Solved]"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by tiachopvutru on 2007-11-04
I'm using Ubuntu 7.10 and graphic card ATI Radeon XPress 200G  (it's 200 something but can't say for sure if it's G)

Here's the lspci output

```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem

```


Anyway, when I restarted from Windows to Ubuntu today, I received message of not being able to detect video card. Right now I'm running 800 x 600, which is the max resolution I can get, and it seriously is hurting my eyes... Anyway, anyone know how I can get Ubuntu to detect my graphic card again? Now I can't enable Compiz either...


EDIT:

nvm... did **sudo dpkg-reconfigure xserver-xorg** and did the whole bunch of pressing Enter, then restart and it went back to normal... Wonder how though, lol...

---

