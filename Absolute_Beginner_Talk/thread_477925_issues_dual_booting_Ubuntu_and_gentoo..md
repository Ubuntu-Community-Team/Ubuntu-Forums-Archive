---
title: "issues dual booting Ubuntu and gentoo."
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-06-18
I've gotten grub all set up to work, but gentoo seems to be failing. When i boot it up, it'l go through a normal procedure, then tell me that the display manager failed to load. Then all i get is a command prompt.

I've posted this on the gentoo forums, but they seem to be unresponsive (nothing all day)

when i type 

```
sudo gedit /vars/log/Xorg.0.log
``` 

this is what i get

```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux MykolaUbuntu 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
   Before reporting problems, check http://wiki.x.org
   to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
   (++) from command line, (!!) notice, (II) informational,
   (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jun 18 14:47:12 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation GeForce 7300 LE"
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
(II) PCI: 00:00:0: chip 8086,29a0 card 1028,01dd rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,29a1 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:19:0: chip 8086,104c card 1028,01dd rev 02 class 02,00,00 hdr 00
(II) PCI: 00:1a:0: chip 8086,2834 card 1028,01dd rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1028,01dd rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 1028,01dd rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1028,01dd rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1028,01dd rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev f2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2812 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2820 card 1028,01dd rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 1028,01dd rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2825 card 1028,01dd rev 02 class 01,01,85 hdr 00
(II) PCI: 01:00:0: chip 10de,01d1 card 1028,0405 rev a1 class 03,00,00 hdr 00
(II) PCI: 03:03:0: chip 14f1,2f20 card 14f1,200f rev 00 class 07,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
   [0] -1   0   0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
   [0] -1   0   0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
   [0] -1   0   0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
   [0] -1   0   0xdd000000 - 0xdfefffff (0x2f00000) MX[B]
(II) Bus 1 prefetchable memory range:
   [0] -1   0   0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
   [0] -1   0   0xdcf00000 - 0xdcffffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 I/O range:
   [0] -1   0   0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
   [0] -1   0   0xdce00000 - 0xdcefffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation GeForce 7300 LE rev 161, Mem @ 0xdd000000/24, 0xc0000000/28, 0xde000000/24, BIOS @ 0xdfe00000/17
(II) Addressable bus resource ranges are
   [0] -1   0   0x00000000 - 0xffffffff (0x0) MX[B]
   [1] -1   0   0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
   [0] -1   0   0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
   [1] -1   0   0x000f0000 - 0x000fffff (0x10000) MX[B]
   [2] -1   0   0x000c0000 - 0x000effff (0x30000) MX[B]
   [3] -1   0   0x00000000 - 0x0009ffff (0xa0000) MX[B]
   [4] -1   0   0x0000ffff - 0x0000ffff (0x1) IX[B]
   [5] -1   0   0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
   [0] -1   0   0xdcef0000 - 0xdcefffff (0x10000) MX[B]
   [1] -1   0   0xdffdab00 - 0xdffdabff (0x100) MX[B]
   [2] -1   0   0xff980800 - 0xff980bff (0x400) MX[B]
   [3] -1   0   0xdffdc000 - 0xdffdffff (0x4000) MX[B]
   [4] -1   0   0xdffdac00 - 0xdffdafff (0x400) MX[B]
   [5] -1   0   0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
   [6] -1   0   0xdffe0000 - 0xdfffffff (0x20000) MX[B]
   [7] -1   0   0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
   [8] -1   0   0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
   [9] -1   0   0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
   [10] -1   0   0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
   [11] -1   0   0x0000dcf8 - 0x0000dcff (0x8) IX[B]
   [12] -1   0   0x0000ecb0 - 0x0000ecbf (0x10) IX[B]
   [13] -1   0   0x0000fed0 - 0x0000fedf (0x10) IX[B]
   [14] -1   0   0x0000fe70 - 0x0000fe73 (0x4) IX[B]
   [15] -1   0   0x0000fe60 - 0x0000fe67 (0x8) IX[B]
   [16] -1   0   0x0000fe50 - 0x0000fe53 (0x4) IX[B]
   [17] -1   0   0x0000fe40 - 0x0000fe47 (0x8) IX[B]
   [18] -1   0   0x0000ece0 - 0x0000ecff (0x20) IX[B]
   [19] -1   0   0x0000eca0 - 0x0000ecaf (0x10) IX[B]
   [20] -1   0   0x0000fec0 - 0x0000fecf (0x10) IX[B]
   [21] -1   0   0x0000fe30 - 0x0000fe33 (0x4) IX[B]
   [22] -1   0   0x0000fe20 - 0x0000fe27 (0x8) IX[B]
   [23] -1   0   0x0000fe10 - 0x0000fe13 (0x4) IX[B]
   [24] -1   0   0x0000fe00 - 0x0000fe07 (0x8) IX[B]
   [25] -1   0   0x0000ff40 - 0x0000ff5f (0x20) IX[B]
   [26] -1   0   0x0000ff60 - 0x0000ff7f (0x20) IX[B]
   [27] -1   0   0x0000ff80 - 0x0000ff9f (0x20) IX[B]
   [28] -1   0   0x0000ff00 - 0x0000ff1f (0x20) IX[B]
   [29] -1   0   0x0000ff20 - 0x0000ff3f (0x20) IX[B]
   [30] -1   0   0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
   [0] -1   0   0xdcef0000 - 0xdcefffff (0x10000) MX[B]
   [1] -1   0   0xdffdab00 - 0xdffdabff (0x100) MX[B]
   [2] -1   0   0xff980800 - 0xff980bff (0x400) MX[B]
   [3] -1   0   0xdffdc000 - 0xdffdffff (0x4000) MX[B]
   [4] -1   0   0xdffdac00 - 0xdffdafff (0x400) MX[B]
   [5] -1   0   0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
   [6] -1   0   0xdffe0000 - 0xdfffffff (0x20000) MX[B]
   [7] -1   0   0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
   [8] -1   0   0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
   [9] -1   0   0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
   [10] -1   0   0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
   [11] -1   0   0x0000dcf8 - 0x0000dcff (0x8) IX[B]
   [12] -1   0   0x0000ecb0 - 0x0000ecbf (0x10) IX[B]
   [13] -1   0   0x0000fed0 - 0x0000fedf (0x10) IX[B]
   [14] -1   0   0x0000fe70 - 0x0000fe73 (0x4) IX[B]
   [15] -1   0   0x0000fe60 - 0x0000fe67 (0x8) IX[B]
   [16] -1   0   0x0000fe50 - 0x0000fe53 (0x4) IX[B]
   [17] -1   0   0x0000fe40 - 0x0000fe47 (0x8) IX[B]
   [18] -1   0   0x0000ece0 - 0x0000ecff (0x20) IX[B]
   [19] -1   0   0x0000eca0 - 0x0000ecaf (0x10) IX[B]
   [20] -1   0   0x0000fec0 - 0x0000fecf (0x10) IX[B]
   [21] -1   0   0x0000fe30 - 0x0000fe33 (0x4) IX[B]
   [22] -1   0   0x0000fe20 - 0x0000fe27 (0x8) IX[B]
   [23] -1   0   0x0000fe10 - 0x0000fe13 (0x4) IX[B]
   [24] -1   0   0x0000fe00 - 0x0000fe07 (0x8) IX[B]
   [25] -1   0   0x0000ff40 - 0x0000ff5f (0x20) IX[B]
   [26] -1   0   0x0000ff60 - 0x0000ff7f (0x20) IX[B]
   [27] -1   0   0x0000ff80 - 0x0000ff9f (0x20) IX[B]
   [28] -1   0   0x0000ff00 - 0x0000ff1f (0x20) IX[B]
   [29] -1   0   0x0000ff20 - 0x0000ff3f (0x20) IX[B]
   [30] -1   0   0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
   [0] -1   0   0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
   [1] -1   0   0x000f0000 - 0x000fffff (0x10000) MX[B]
   [2] -1   0   0x000c0000 - 0x000effff (0x30000) MX[B]
   [3] -1   0   0x00000000 - 0x0009ffff (0xa0000) MX[B]
   [4] -1   0   0x0000ffff - 0x0000ffff (0x1) IX[B]
   [5] -1   0   0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
   [0] -1   0   0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
   [1] -1   0   0x000f0000 - 0x000fffff (0x10000) MX[B]
   [2] -1   0   0x000c0000 - 0x000effff (0x30000) MX[B]
   [3] -1   0   0x00000000 - 0x0009ffff (0xa0000) MX[B]
   [4] -1   0   0xdcef0000 - 0xdcefffff (0x10000) MX[B]
   [5] -1   0   0xdffdab00 - 0xdffdabff (0x100) MX[B]
   [6] -1   0   0xff980800 - 0xff980bff (0x400) MX[B]
   [7] -1   0   0xdffdc000 - 0xdffdffff (0x4000) MX[B]
   [8] -1   0   0xdffdac00 - 0xdffdafff (0x400) MX[B]
   [9] -1   0   0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
   [10] -1   0   0xdffe0000 - 0xdfffffff (0x20000) MX[B]
   [11] -1   0   0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
   [12] -1   0   0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
   [13] -1   0   0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
   [14] -1   0   0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
   [15] -1   0   0x0000ffff - 0x0000ffff (0x1) IX[B]
   [16] -1   0   0x00000000 - 0x000000ff (0x100) IX[B]
   [17] -1   0   0x0000dcf8 - 0x0000dcff (0x8) IX[B]
   [18] -1   0   0x0000ecb0 - 0x0000ecbf (0x10) IX[B]
   [19] -1   0   0x0000fed0 - 0x0000fedf (0x10) IX[B]
   [20] -1   0   0x0000fe70 - 0x0000fe73 (0x4) IX[B]
   [21] -1   0   0x0000fe60 - 0x0000fe67 (0x8) IX[B]
   [22] -1   0   0x0000fe50 - 0x0000fe53 (0x4) IX[B]
   [23] -1   0   0x0000fe40 - 0x0000fe47 (0x8) IX[B]
   [24] -1   0   0x0000ece0 - 0x0000ecff (0x20) IX[B]
   [25] -1   0   0x0000eca0 - 0x0000ecaf (0x10) IX[B]
   [26] -1   0   0x0000fec0 - 0x0000fecf (0x10) IX[B]
   [27] -1   0   0x0000fe30 - 0x0000fe33 (0x4) IX[B]
   [28] -1   0   0x0000fe20 - 0x0000fe27 (0x8) IX[B]
   [29] -1   0   0x0000fe10 - 0x0000fe13 (0x4) IX[B]
   [30] -1   0   0x0000fe00 - 0x0000fe07 (0x8) IX[B]
   [31] -1   0   0x0000ff40 - 0x0000ff5f (0x20) IX[B]
   [32] -1   0   0x0000ff60 - 0x0000ff7f (0x20) IX[B]
   [33] -1   0   0x0000ff80 - 0x0000ff9f (0x20) IX[B]
   [34] -1   0   0x0000ff00 - 0x0000ff1f (0x20) IX[B]
   [35] -1   0   0x0000ff20 - 0x0000ff3f (0x20) IX[B]
   [36] -1   0   0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
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
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
   compiled for 4.0.2, module version = 1.0.9631
   Module class: X.Org Server Extension
   ABI class: X.Org Server Extension, version 0.1
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
   compiled for 4.0.2, module version = 1.0.9631
   Module class: X.Org Video Driver
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
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
   compiled for 7.2.0, module version = 1.0.0
   ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
   compiled for 7.2.0, module version = 0.1.0
   ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
   [0] -1   0   0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
   [1] -1   0   0x000f0000 - 0x000fffff (0x10000) MX[B]
   [2] -1   0   0x000c0000 - 0x000effff (0x30000) MX[B]
   [3] -1   0   0x00000000 - 0x0009ffff (0xa0000) MX[B]
   [4] -1   0   0xdcef0000 - 0xdcefffff (0x10000) MX[B]
   [5] -1   0   0xdffdab00 - 0xdffdabff (0x100) MX[B]
   [6] -1   0   0xff980800 - 0xff980bff (0x400) MX[B]
   [7] -1   0   0xdffdc000 - 0xdffdffff (0x4000) MX[B]
   [8] -1   0   0xdffdac00 - 0xdffdafff (0x400) MX[B]
   [9] -1   0   0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
   [10] -1   0   0xdffe0000 - 0xdfffffff (0x20000) MX[B]
   [11] -1   0   0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
   [12] -1   0   0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
   [13] -1   0   0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
   [14] -1   0   0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
   [15] -1   0   0x0000ffff - 0x0000ffff (0x1) IX[B]
   [16] -1   0   0x00000000 - 0x000000ff (0x100) IX[B]
   [17] -1   0   0x0000dcf8 - 0x0000dcff (0x8) IX[B]
   [18] -1   0   0x0000ecb0 - 0x0000ecbf (0x10) IX[B]
   [19] -1   0   0x0000fed0 - 0x0000fedf (0x10) IX[B]
   [20] -1   0   0x0000fe70 - 0x0000fe73 (0x4) IX[B]
   [21] -1   0   0x0000fe60 - 0x0000fe67 (0x8) IX[B]
   [22] -1   0   0x0000fe50 - 0x0000fe53 (0x4) IX[B]
   [23] -1   0   0x0000fe40 - 0x0000fe47 (0x8) IX[B]
   [24] -1   0   0x0000ece0 - 0x0000ecff (0x20) IX[B]
   [25] -1   0   0x0000eca0 - 0x0000ecaf (0x10) IX[B]
   [26] -1   0   0x0000fec0 - 0x0000fecf (0x10) IX[B]
   [27] -1   0   0x0000fe30 - 0x0000fe33 (0x4) IX[B]
   [28] -1   0   0x0000fe20 - 0x0000fe27 (0x8) IX[B]
   [29] -1   0   0x0000fe10 - 0x0000fe13 (0x4) IX[B]
   [30] -1   0   0x0000fe00 - 0x0000fe07 (0x8) IX[B]
   [31] -1   0   0x0000ff40 - 0x0000ff5f (0x20) IX[B]
   [32] -1   0   0x0000ff60 - 0x0000ff7f (0x20) IX[B]
   [33] -1   0   0x0000ff80 - 0x0000ff9f (0x20) IX[B]
   [34] -1   0   0x0000ff00 - 0x0000ff1f (0x20) IX[B]
   [35] -1   0   0x0000ff20 - 0x0000ff3f (0x20) IX[B]
   [36] -1   0   0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
(II) resource ranges after probing:
   [0] -1   0   0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
   [1] -1   0   0x000f0000 - 0x000fffff (0x10000) MX[B]
   [2] -1   0   0x000c0000 - 0x000effff (0x30000) MX[B]
   [3] -1   0   0x00000000 - 0x0009ffff (0xa0000) MX[B]
   [4] -1   0   0xdcef0000 - 0xdcefffff (0x10000) MX[B]
   [5] -1   0   0xdffdab00 - 0xdffdabff (0x100) MX[B]
   [6] -1   0   0xff980800 - 0xff980bff (0x400) MX[B]
   [7] -1   0   0xdffdc000 - 0xdffdffff (0x4000) MX[B]
   [8] -1   0   0xdffdac00 - 0xdffdafff (0x400) MX[B]
   [9] -1   0   0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
   [10] -1   0   0xdffe0000 - 0xdfffffff (0x20000) MX[B]
   [11] -1   0   0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
   [12] -1   0   0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
   [13] -1   0   0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
   [14] -1   0   0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
   [15] 0   0   0x000a0000 - 0x000affff (0x10000) MS[B]
   [16] 0   0   0x000b0000 - 0x000b7fff (0x8000) MS[B]
   [17] 0   0   0x000b8000 - 0x000bffff (0x8000) MS[B]
   [18] -1   0   0x0000ffff - 0x0000ffff (0x1) IX[B]
   [19] -1   0   0x00000000 - 0x000000ff (0x100) IX[B]
   [20] -1   0   0x0000dcf8 - 0x0000dcff (0x8) IX[B]
   [21] -1   0   0x0000ecb0 - 0x0000ecbf (0x10) IX[B]
   [22] -1   0   0x0000fed0 - 0x0000fedf (0x10) IX[B]
   [23] -1   0   0x0000fe70 - 0x0000fe73 (0x4) IX[B]
   [24] -1   0   0x0000fe60 - 0x0000fe67 (0x8) IX[B]
   [25] -1   0   0x0000fe50 - 0x0000fe53 (0x4) IX[B]
   [26] -1   0   0x0000fe40 - 0x0000fe47 (0x8) IX[B]
   [27] -1   0   0x0000ece0 - 0x0000ecff (0x20) IX[B]
   [28] -1   0   0x0000eca0 - 0x0000ecaf (0x10) IX[B]
   [29] -1   0   0x0000fec0 - 0x0000fecf (0x10) IX[B]
   [30] -1   0   0x0000fe30 - 0x0000fe33 (0x4) IX[B]
   [31] -1   0   0x0000fe20 - 0x0000fe27 (0x8) IX[B]
   [32] -1   0   0x0000fe10 - 0x0000fe13 (0x4) IX[B]
   [33] -1   0   0x0000fe00 - 0x0000fe07 (0x8) IX[B]
   [34] -1   0   0x0000ff40 - 0x0000ff5f (0x20) IX[B]
   [35] -1   0   0x0000ff60 - 0x0000ff7f (0x20) IX[B]
   [36] -1   0   0x0000ff80 - 0x0000ff9f (0x20) IX[B]
   [37] -1   0   0x0000ff00 - 0x0000ff1f (0x20) IX[B]
   [38] -1   0   0x0000ff20 - 0x0000ff3f (0x20) IX[B]
   [39] -1   0   0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
   [40] 0   0   0x000003b0 - 0x000003bb (0xc) IS[B]
   [41] 0   0   0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 LE at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.49.09
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 LE at PCI:1:0:0:
(--) NVIDIA(0):     Proview (CRT-0)
(--) NVIDIA(0): Proview (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1440x1440"; removing.
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1680x1050"
(II) NVIDIA(0):     "1440x900"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) NVIDIA(0): DPI set to (90, 88); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
   [0] 0   0   0xde000000 - 0xdeffffff (0x1000000) MX[B]
   [1] 0   0   0xc0000000 - 0xcfffffff (0x10000000) MX[B]
   [2] 0   0   0xdd000000 - 0xddffffff (0x1000000) MX[B]
   [3] -1   0   0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
   [4] -1   0   0x000f0000 - 0x000fffff (0x10000) MX[B]
   [5] -1   0   0x000c0000 - 0x000effff (0x30000) MX[B]
   [6] -1   0   0x00000000 - 0x0009ffff (0xa0000) MX[B]
   [7] -1   0   0xdcef0000 - 0xdcefffff (0x10000) MX[B]
   [8] -1   0   0xdffdab00 - 0xdffdabff (0x100) MX[B]
   [9] -1   0   0xff980800 - 0xff980bff (0x400) MX[B]
   [10] -1   0   0xdffdc000 - 0xdffdffff (0x4000) MX[B]
   [11] -1   0   0xdffdac00 - 0xdffdafff (0x400) MX[B]
   [12] -1   0   0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
   [13] -1   0   0xdffe0000 - 0xdfffffff (0x20000) MX[B]
   [14] -1   0   0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
   [15] -1   0   0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
   [16] -1   0   0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
   [17] -1   0   0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
   [18] 0   0   0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
   [19] 0   0   0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
   [20] 0   0   0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
   [21] -1   0   0x0000ffff - 0x0000ffff (0x1) IX[B]
   [22] -1   0   0x00000000 - 0x000000ff (0x100) IX[B]
   [23] -1   0   0x0000dcf8 - 0x0000dcff (0x8) IX[B]
   [24] -1   0   0x0000ecb0 - 0x0000ecbf (0x10) IX[B]
   [25] -1   0   0x0000fed0 - 0x0000fedf (0x10) IX[B]
   [26] -1   0   0x0000fe70 - 0x0000fe73 (0x4) IX[B]
   [27] -1   0   0x0000fe60 - 0x0000fe67 (0x8) IX[B]
   [28] -1   0   0x0000fe50 - 0x0000fe53 (0x4) IX[B]
   [29] -1   0   0x0000fe40 - 0x0000fe47 (0x8) IX[B]
   [30] -1   0   0x0000ece0 - 0x0000ecff (0x20) IX[B]
   [31] -1   0   0x0000eca0 - 0x0000ecaf (0x10) IX[B]
   [32] -1   0   0x0000fec0 - 0x0000fecf (0x10) IX[B]
   [33] -1   0   0x0000fe30 - 0x0000fe33 (0x4) IX[B]
   [34] -1   0   0x0000fe20 - 0x0000fe27 (0x8) IX[B]
   [35] -1   0   0x0000fe10 - 0x0000fe13 (0x4) IX[B]
   [36] -1   0   0x0000fe00 - 0x0000fe07 (0x8) IX[B]
   [37] -1   0   0x0000ff40 - 0x0000ff5f (0x20) IX[B]
   [38] -1   0   0x0000ff60 - 0x0000ff7f (0x20) IX[B]
   [39] -1   0   0x0000ff80 - 0x0000ff9f (0x20) IX[B]
   [40] -1   0   0x0000ff00 - 0x0000ff1f (0x20) IX[B]
   [41] -1   0   0x0000ff20 - 0x0000ff3f (0x20) IX[B]
   [42] -1   0   0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
   [43] 0   0   0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
   [44] 0   0   0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1680x1050"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
   No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
   No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
   No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
```

I don't know how to access that file from within gentoo


i've got an Nvidia GeForce 7300 LE graphics card and it works with the liveCD, just not the installed version.


I'd rather not reinstall (ugh... compiling from source... 11hours) and i'd like to compare gentoo to ubuntu.

any suggestions?

---

### Post by kidders on 2007-06-20
Hi there,

Gentoo & Ubuntu are pretty incomparable, really. In many ways, they're pitched at opposite ends of the user spectrum ... novice vs guru.

Anyhow, you seem to have misconfigured X in one of your Linuxes ... you're referencing a non-existent input device (/dev/input/wacom).

---

### Post by eldepeche on 2007-06-20
Those errors are coming in your Gentoo install? Did you just copy xorg.conf over from Ubuntu? 

If you don't have a Wacom tablet, you can simpy delete those stanzas from xorg.conf, as well as the lines referring to the tablet in the ServerLayout section.

---

