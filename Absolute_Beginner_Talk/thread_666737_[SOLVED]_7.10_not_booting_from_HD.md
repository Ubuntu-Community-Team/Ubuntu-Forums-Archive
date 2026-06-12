---
title: "[SOLVED] 7.10 not booting from HD"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Jeztastic on 2008-01-13
Hi.

Am posting this from Live CD.

When I boot from HD, I get some initial text on screen, and some HD activity, but the computer will then hang on a black screen.

This occurred a while ago, then fixed itself :confused:. 

Anyway, I had been trying to change the drivers of my graphics card using [this (click here)]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") HOWTO. 

Anyway, I have changed xorg.conf back to this:

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	Busid		"PCI:1:5:0"
```

As it's the same as the Live CD. Still no good.

Output of lspci of my HD:

```

ubuntu@ubuntu:/media/disk$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```


Please help!

---

### Post by blueridgedog on 2008-01-13
If you boot to a black screen (not using the live CD), can you press CTR+ALT+BACKSPACE and tell me if you get a terminal?

If you get a terminal, try

sudo dpkg-reconfigure xserver-xorg

---

### Post by blueridgedog on 2008-01-13
Removing duplicate post

---

### Post by Jeztastic on 2008-01-13
Didn't get the terminal from hanging screen, but I reconfigured the x-server via recovery mode, and that's fixed it. 

Many thanks, you are a star. :)

---

