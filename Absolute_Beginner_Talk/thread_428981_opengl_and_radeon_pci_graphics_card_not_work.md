---
title: "opengl and radeon pci graphics card not work"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by dpbohlmann on 2007-04-30
I went through the help.ubunto.com BinraryDriversHowTo doc, but to no avail.
I have a Radeon 9200 graphics PCI card installed in a Gateway 614GE desktop, Ubuntu Fiesty is installed on slave HD.
If, in my xorg.conf, I say the driver for my Radeon is "vesa", my display works, though not the OpenGL test fgl_glxgears. The pertinent parts of this file are:
[COLOR="Blue"]
Section "Device"
Identifier "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
Driver "vesa"
BusID "PCI:0:5:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
Monitor "Generic Monitor"
DefaultDepth 24
. . . .
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection
[/COLOR]

I went through the help doc file, did what it said, and the various tools edited the xorg.conf file. But, when I would boot, I kept getting an 'X graphics' error, complaining about missing devices for PCI 0:5:0 and 0:5:1. My Radeon is at PCI 0:5:0, and the PCI device list shows a secondary Radeon at PCI 0:5:1, though I only have one Radeon card, which confuses me.
Any, I took the hint and edited the xorg.conf to say something about PCI 0:5:0, which is here:

[COLOR="Blue"]Section "Monitor"
Identifier "aticonfig-Monitor[0]"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
BusID "PCI:0:5:0"
EndSection

Section "Device"
Identifier "aticonfig-Device[1]"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
BusID "PCI:0:5:1"
EndSection
Section "Screen"
Identifier "aticonfig-Screen[0]"
Device "aticonfig-Device[0]"
Monitor "aticonfig-Monitor[0]"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "0"
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "aticonfig-Screen[0]"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection
[/COLOR]

I tried it with the reference to my aticonfig-Device[0] only, and then also added the aticonfigDevice[1] reference. Both give me the same 'X system error as follows:


X[COLOR="Red"] Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ozzie-desktop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr 26 22:45:24 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) | |-->Monitor "aticonfig-Monitor[0]"
(**) | |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
Entry deleted from font path.
(**) FontPath set to:
/usr/share/fonts/X11/misc,
/usr/share/fonts/X11/100dpi/:unscaled,
/usr/share/fonts/X11/75dpi/:unscaled,
/usr/share/fonts/X11/Type1,
/usr/share/fonts/X11/100dpi,
/usr/share/fonts/X11/75dpi,
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
/usr/share/fonts/X11/misc,
/usr/X11R6/lib/X11/fonts/misc,
/usr/share/fonts/X11/cyrillic,
/usr/share/fonts/X11/100dpi/:unscaled,
/usr/share/fonts/X11/75dpi/:unscaled,
/usr/share/fonts/X11/Type1,
/usr/X11R6/lib/X11/fonts/Type1,
/usr/share/fonts/X11/100dpi,
/usr/share/fonts/X11/75dpi,
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
X.Org ANSI C Emulation: 0.3
X.Org Video Driver: 1.1
X.Org XInput driver : 0.7
X.Org Server Extension : 0.3
X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
compiled for 7.2.0, module version = 1.0.0
ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0204 card 1106,3204 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:7: chip 1106,7204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 1002,5960 card 1002,2002 rev 01 class 03,00,00 hdr 80
(II) PCI: 00:05:1: chip 1002,5940 card 1002,2003 rev 01 class 03,80,00 hdr 00
(II) PCI: 00:07:0: chip 14f1,2f20 card 14f1,2000 rev 00 class 07,80,00 hdr 00
(II) PCI: 00:0e:0: chip 1106,3044 card 1462,7410 rev 80 class 0c,00,10 hdr 00
(II) PCI: 00:0f:0: chip 1106,0571 card 1462,7410 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1462,7410 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1462,7410 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1462,7410 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1462,7410 rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1462,7410 rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1106,3227 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1462,7410 rev 60 class 04,01,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1462,021c rev 78 class 02,00,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1106,3108 card 1462,7410 rev 01 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
[0] -1 0 0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
[0] -1 0 0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 0 prefetchable memory range:
[0] -1 0 0x00000000 - 0xffffffff (0x0) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
[0] -1 0 0xcde00000 - 0xcfefffff (0x2100000) MX[b]
(II) Bus 1 prefetchable memory range:
[0] -1 0 0xa5d00000 - 0xadcfffff (0x8000000) MX[b]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:5:0) ATI Technologies Inc RV280 [Radeon 9200 PRO] rev 1, Mem @ 0xb8000000/27, 0xcffe0000/16, I/O @ 0xe800/8, BIOS @ 0xcffc0000/17
(--) PCI: (0:5:1) ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) rev 1, Mem @ 0xc0000000/27, 0xcfff0000/16
(--) PCI:*(1:0:0) unknown vendor (0x1106) unknown chipset (0x310 rev 1, Mem @ 0xa8000000/26, 0xce000000/24, BIOS @ 0xcfef0000/16
(II) Addressable bus resource ranges are
[0] -1 0 0x00000000 - 0xffffffff (0x0) MX[b]
[1] -1 0 0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) OS-reported resource ranges:
[0] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[5] -1 0 0x00000000 - 0x000000ff (0x100) IX[b]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffffff
(II) Active PCI resource ranges:
[0] -1 0 0xcffaf500 - 0xcffaf5ff (0x100) MX[b]
[1] -1 0 0xcffaf600 - 0xcffaf6ff (0x100) MX[b]
[2] -1 0 0xcffaf800 - 0xcffaffff (0x800) MX[b]
[3] -1 0 0xcffb0000 - 0xcffbffff (0x10000) MX[b]
[4] -1 0 0xd0000000 - 0xcfffffff (0x0) MX[b]O
[5] -1 0 0xcfef0000 - 0xcfefffff (0x10000) MX[b](B)
[6] -1 0 0xce000000 - 0xceffffff (0x1000000) MX[b](B)
[7] -1 0 0xa8000000 - 0xabffffff (0x4000000) MX[b](B)
[8] -1 0 0xcfff0000 - 0xcfffffff (0x10000) MX[b](B)
[9] -1 0 0xc0000000 - 0xc7ffffff (0x8000000) MX[b](B)
[10] -1 0 0x0000cc00 - 0x0000ccff (0x100) IX[b]
[11] -1 0 0x0000d000 - 0x0000d0ff (0x100) IX[b]
[12] -1 0 0x0000e000 - 0x0000e01f (0x20) IX[b]
[13] -1 0 0x0000dc00 - 0x0000dc1f (0x20) IX[b]
[14] -1 0 0x0000d800 - 0x0000d81f (0x20) IX[b]
[15] -1 0 0x0000d400 - 0x0000d41f (0x20) IX[b]
[16] -1 0 0x0000fc00 - 0x0000fc0f (0x10) IX[b]
[17] -1 0 0x0000e400 - 0x0000e47f (0x80) IX[b]
[18] -1 0 0x0000ec00 - 0x0000ec07 (0x IX[b]
(II) Inactive PCI resource ranges:
[0] -1 0 0xcffc0000 - 0xcffdffff (0x20000) MX[b](B)
[1] -1 0 0xcffe0000 - 0xcffeffff (0x10000) MX[b](B)
[2] -1 0 0xb8000000 - 0xbfffffff (0x8000000) MX[b](B)
[3] -1 0 0x0000e800 - 0x0000e8ff (0x100) IX[b](B)
(II) Active PCI resource ranges after removing overlaps:
[0] -1 0 0xcffaf500 - 0xcffaf5ff (0x100) MX[b]
[1] -1 0 0xcffaf600 - 0xcffaf6ff (0x100) MX[b]
[2] -1 0 0xcffaf800 - 0xcffaffff (0x800) MX[b]
[3] -1 0 0xcffb0000 - 0xcffbffff (0x10000) MX[b]
[4] -1 0 0xd0000000 - 0xcfffffff (0x0) MX[b]O
[5] -1 0 0xcfef0000 - 0xcfefffff (0x10000) MX[b](B)
[6] -1 0 0xce000000 - 0xceffffff (0x1000000) MX[b](B)
[7] -1 0 0xa8000000 - 0xabffffff (0x4000000) MX[b](B)
[8] -1 0 0xcfff0000 - 0xcfffffff (0x10000) MX[b](B)
[9] -1 0 0xc0000000 - 0xc7ffffff (0x8000000) MX[b](B)
[10] -1 0 0x0000cc00 - 0x0000ccff (0x100) IX[b]
[11] -1 0 0x0000d000 - 0x0000d0ff (0x100) IX[b]
[12] -1 0 0x0000e000 - 0x0000e01f (0x20) IX[b]
[13] -1 0 0x0000dc00 - 0x0000dc1f (0x20) IX[b]
[14] -1 0 0x0000d800 - 0x0000d81f (0x20) IX[b]
[15] -1 0 0x0000d400 - 0x0000d41f (0x20) IX[b]
[16] -1 0 0x0000fc00 - 0x0000fc0f (0x10) IX[b]
[17] -1 0 0x0000e400 - 0x0000e47f (0x80) IX[b]
[18] -1 0 0x0000ec00 - 0x0000ec07 (0x IX[b]
(II) Inactive PCI resource ranges after removing overlaps:
[0] -1 0 0xcffc0000 - 0xcffdffff (0x20000) MX[b](B)
[1] -1 0 0xcffe0000 - 0xcffeffff (0x10000) MX[b](B)
[2] -1 0 0xb8000000 - 0xbfffffff (0x8000000) MX[b](B)
[3] -1 0 0x0000e800 - 0x0000e8ff (0x100) IX[b](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
[0] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[5] -1 0 0x00000000 - 0x000000ff (0x100) IX[b]
(II) All system resource ranges:
[0] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0xcffaf500 - 0xcffaf5ff (0x100) MX[b]
[5] -1 0 0xcffaf600 - 0xcffaf6ff (0x100) MX[b]
[6] -1 0 0xcffaf800 - 0xcffaffff (0x800) MX[b]
[7] -1 0 0xcffb0000 - 0xcffbffff (0x10000) MX[b]
[8] -1 0 0xd0000000 - 0xcfffffff (0x0) MX[b]O
[9] -1 0 0xcfef0000 - 0xcfefffff (0x10000) MX[b](B)
[10] -1 0 0xce000000 - 0xceffffff (0x1000000) MX[b](B)
[11] -1 0 0xa8000000 - 0xabffffff (0x4000000) MX[b](B)
[12] -1 0 0xcfff0000 - 0xcfffffff (0x10000) MX[b](B)
[13] -1 0 0xc0000000 - 0xc7ffffff (0x8000000) MX[b](B)
[14] -1 0 0xcffc0000 - 0xcffdffff (0x20000) MX[b](B)
[15] -1 0 0xcffe0000 - 0xcffeffff (0x10000) MX[b](B)
[16] -1 0 0xb8000000 - 0xbfffffff (0x8000000) MX[b](B)
[17] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[18] -1 0 0x00000000 - 0x000000ff (0x100) IX[b]
[19] -1 0 0x0000cc00 - 0x0000ccff (0x100) IX[b]
[20] -1 0 0x0000d000 - 0x0000d0ff (0x100) IX[b]
[21] -1 0 0x0000e000 - 0x0000e01f (0x20) IX[b]
[22] -1 0 0x0000dc00 - 0x0000dc1f (0x20) IX[b]
[23] -1 0 0x0000d800 - 0x0000d81f (0x20) IX[b]
[24] -1 0 0x0000d400 - 0x0000d41f (0x20) IX[b]
[25] -1 0 0x0000fc00 - 0x0000fc0f (0x10) IX[b]
[26] -1 0 0x0000e400 - 0x0000e47f (0x80) IX[b]
[27] -1 0 0x0000ec00 - 0x0000ec07 (0x IX[b]
[28] -1 0 0x0000e800 - 0x0000e8ff (0x100) IX[b](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
compiled for 7.2.0, module version = 1.2.0
ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
compiled for 7.2.0, module version = 1.0.0
ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
compiled for 7.2.0, module version = 1.0.0
ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
compiled for 7.2.0, module version = 1.0.0
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
compiled for 7.2.0, module version = 2.1.0
Module class: X.Org Font Renderer
ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
compiled for 7.2.0, module version = 1.0.0
ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
compiled for 7.2.0, module version = 1.0.0
ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
compiled for 7.2.0, module version = 1.1.0
ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
compiled for 7.1.0, module version = 8.34.8
Module class: X.Org Video Driver
ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
compiled for 7.2.0, module version = 1.1.0
Module class: X.Org XInput Driver
ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
compiled for 7.2.0, module version = 1.1.1
Module class: X.Org XInput Driver
ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
compiled for 4.3.99.902, module version = 1.0.0
Module class: X.Org XInput Driver
ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.34.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.34g1
(II) ATI Proprietary Linux Driver Build Date: Feb 20 2007 11:49:19
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.34.1.1.2.3-driver-lnx-x86-x86_64-327152
(WW) fglrx: No matching Device section for instance (BusID PCI:0:5:1) found
(EE) No devices detected.

Fatal server error:
no screens found[/COLOR]

What should I do????
TX.

---

### Post by mikeyphi on 2007-05-01
If you haven't already tried this advice - it might help:

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

Good luck!!

---

### Post by dpbohlmann on 2007-05-01
Been there, done that.
Tried it again to no avail.
The problem is the complaint about no device mechanism for PCI device 0:5:0 (the Radeon) and 0:5:1 (a 'secondary' Radeon, which I do not have installed but lspci shows.
Thanx anyway.
More ideas?

---

