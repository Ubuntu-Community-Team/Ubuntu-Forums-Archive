---
title: "Duplicates on gnome panel"
date: 2013-10-17
forum: Any Other OS
---

### Post by ac1d2 on 2013-10-17
Alright, I'm doing an all-out assualt on trying to get this issue fixed.
Posting on every forum possible and reading like crazy.

The issue is pretty simple. I have duplicate desktops and/or entries on my gnome panel(top, black bar).

[ATTACH=CONFIG]247003[/ATTACH]

[ATTACH=CONFIG]247005[/ATTACH]

As you can see the duplicates increase and the screen space diminishes  after each subsequent restart, until my primary desktop is left a black  screen.

I did a fresh install of Debian Wheezy. Put in new drivers via the description provided here:

[https://wiki.debian.org/ATIProprietary](https://wiki.debian.org/ATIProprietary)

I ran the follwoing to generate a xorg for multiple video cards:

aticonfig --adapter=all --initial

  
Here's a current Xorg.conf:[URL="http://www.linuxquestions.org/questions/attachment.php?attachmentid=13748&d=1381991835"]

[/URL]```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[1]-0"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[1]-0"
    Device     "aticonfig-Device[1]-0"
    Monitor    "aticonfig-Monitor[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```[URL="http://www.linuxquestions.org/questions/attachment.php?attachmentid=13748&d=1381991835"]
[/URL]
Here's a current lspci:

```
root@D3b1AN:~# lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation P67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cypress XT [Radeon HD 5870]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cypress HDMI Audio [Radeon HD 5800 Series]
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cedar PRO [Radeon HD 5450/6350]
02:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cedar HDMI Audio [Radeon HD 5400/6300 Series]
04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
05:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 01)
06:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
07:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
```


This a desktop issue. Yes I understand that I'm a debian user, but mod's please dont move my thread. As it applies to the desktop env. and has nothing what so ever to do with my distro.



My system:
Debian Wheezy 64bit
Gnome 3
Radeon 5870
Radeon 5450
4-27" lcd's (2-AOC & 2-Viewsonic)
1-40" led tv

---

### Post by ac1d2 on 2013-10-17
If your interested and/or it applies here's how my current desktop sits:

[ATTACH=CONFIG]247004[/ATTACH]

---

### Post by Elfy on 2013-10-17
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

