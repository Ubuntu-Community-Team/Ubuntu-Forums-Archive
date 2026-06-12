---
title: "Graphics card"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by jaytwokay on 2007-08-01
I believe that my graphic card is not installed on my computer. Every time I try and use the desktop effects my screen goes white until I disable them.

I'm not sure how to check which drivers I need or how to install them.

When I type in lspci I get

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


I am still getting use to linux so any help would be appreciated.

---

### Post by tchoklat on 2007-08-01
If you are using Feisty look at the 'sticky' by Mike on installing ATI drivers

---

### Post by carloslosgrande on 2007-08-01
Hi, I have an ATI Radeon X600 pci card and it works just fine for everything EXCEPT the desktop effects, so I don't use them.

---

### Post by jaytwokay on 2007-08-01
Ok, So I installed the drivers and it was successful. but still cannot get desktop effects to work. Can anyone help?

---

### Post by carloslosgrande on 2007-08-01
[FONT="Comic Sans MS"]I guess the next step is for you to have a look at Brunellus's sticky at the beginners page. I'm certainly no expert in this stuff.[/FONT]
[FONT="Comic Sans MS"]good luck[/FONT]

---

### Post by jaytwokay on 2007-08-01
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]I guess the next step is for you to have a look at Brunellus's sticky at the beginners page. I'm certainly no expert in this stuff.[/FONT]
[FONT="Comic Sans MS"]good luck[/FONT]

I took a look, but still no luck......

I'm pretty sure my dirvers are installed right I type in 'fglrxinfo' and get the following
( I have the Radeon XPRESS 200M) 

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)

---

### Post by jaytwokay on 2007-08-01
I've been trying different ways to get my graphics card to work with no work.......

Now when I type fglrxinfo I get
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

---

### Post by jaytwokay on 2007-08-04
up

---

