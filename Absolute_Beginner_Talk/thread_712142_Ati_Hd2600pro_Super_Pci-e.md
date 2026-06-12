---
title: "Ati Hd2600pro Super Pci-e"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by rockinlinux on 2008-03-01
I just built a new computer, I need to install the ATI drivers for my card. here is my lspci for the card:

```
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Unknown device [1
```

I have read a lot about this but I have read about a lot of people having problems and i see so many different ways to install these drivers...im just confused..


here are my system specs:

MOBO: MSI p35 Neo2
Proc: intel 6600 duo2 quad
Graphics: ATI HD2600Pro Super PCI-E 512MB DDR2 HDMI AVI

Any help would be great, I would like to get compiz running good like i had it on my laptop before.

thanks in advance! :)

---

### Post by startherepodcast on 2008-03-01
There are GPLed drivers shipped with Ubuntu, but if you want to run compiz fusion, you will need the proprietary drivers (fglrx). They should install with the restricted drivers manager in System->Administration. You might want to check out [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) to get the newest, more performant drivers that don't need XGL (3D acceleration in software). I run the newest drivers on my lappy, they run OK, you know how linux drivers are :()

Hope that helped

Leon

---

### Post by rockinlinux on 2008-03-03
I have never configured a graphics card in linux so im kinda lost. I went to my restricted drivers and installed that but it messed everything up bad.,...i have like 4 different screen that were narrow and tall. After i installed that driver i rebooted and linux went into low res mode...i tried to pick my monitor but it was not there...i picked my res but like i say it was not good. even on the "4 desktops" the quality was very poor.

What else should i try?

thanks again :)

just to be sure to guys know...this is not in a laptop...its a PCI-E card.

---

### Post by rockinlinux on 2008-03-04
anyone else have any ideas?

---

### Post by rockinlinux on 2008-03-06
gotta bump it...i still have not figured it out.

---

### Post by kellemes on 2008-03-07
Please post the contents of
/etc/X11/xorg.conf
/var/log/Xorg.0.log

---

### Post by rockinlinux on 2008-03-07
Section "Device"
	Identifier	"ATI Technologies Inc ATI Default Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"VA903 SERIES"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"VA903 SERIES"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection

---

### Post by rockinlinux on 2008-03-07
I cant post the otehr file....im not sure waht parts you need me to posta dn if i try the whole thing the forum gives me a :

You have included 39 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

Images include use of smilies, the vB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

message

---

### Post by rockinlinux on 2008-03-07
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux home-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar  7 09:15:05 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "VA903 SERIES"
(**) |   |-->Device "ATI Technologies Inc ATI Default Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81e9800
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,29c0 card 1462,7345 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,29c1 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1a:0: chip 8086,2937 card 1462,7345 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2938 card 1462,7345 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,293c card 1462,7345 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,293e card 1462,735a rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2940 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2948 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:5: chip 8086,294a card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2934 card 1462,7345 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2935 card 1462,7345 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2936 card 1462,7345 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,2939 card 1462,7345 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,293a card 1462,7345 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 92 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2916 card 1462,7345 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2920 card 1462,7345 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,2930 card 1462,7345 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2926 card 1462,7345 rev 02 class 01,01,85 hdr 00
(II) PCI: 01:00:0: chip 1002,9589 card 0000,0000 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,aa08 card 0000,aa08 rev 00 class 04,03,00 hdr 80
(II) PCI: 03:00:0: chip 11ab,6121 card 11ab,6121 rev b1 class 01,01,8f hdr 00
(II) PCI: 04:00:0: chip 10ec,8168 card 1462,345c rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:4), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:5), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x9589) rev 0, Mem @ 0xd0000000/28, 0xfe9f0000/16, I/O @ 0xc000/8, BIOS @ 0xfe9c0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[1] -1	0	0xfeaffc00 - 0xfeafffff (0x400) MX[B]
	[2] -1	0	0xfe9ec000 - 0xfe9effff (0x4000) MX[B]
	[3] -1	0	0xfe8ff400 - 0xfe8ff4ff (0x100) MX[B]
	[4] -1	0	0xfe8ff800 - 0xfe8ffbff (0x400) MX[B]
	[5] -1	0	0xfe8f8000 - 0xfe8fbfff (0x4000) MX[B]
	[6] -1	0	0xfe8ffc00 - 0xfe8fffff (0x400) MX[B]
	[7] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B](B)
	[8] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[11] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[12] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[14] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[16] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[17] -1	0	0x00009480 - 0x0000948f (0x10) IX[B]
	[18] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[19] -1	0	0x00009880 - 0x00009887 (0x8) IX[B]
	[20] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[22] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[23] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[24] -1	0	0x0000a480 - 0x0000a48f (0x10) IX[B]
	[25] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[26] -1	0	0x0000a880 - 0x0000a887 (0x8) IX[B]
	[27] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[28] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[29] -1	0	0x0000b080 - 0x0000b09f (0x20) IX[B]
	[30] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[31] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[32] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[33] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[34] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[35] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[1] -1	0	0xfeaffc00 - 0xfeafffff (0x400) MX[B]
	[2] -1	0	0xfe9ec000 - 0xfe9effff (0x4000) MX[B]
	[3] -1	0	0xfe8ff400 - 0xfe8ff4ff (0x100) MX[B]
	[4] -1	0	0xfe8ff800 - 0xfe8ffbff (0x400) MX[B]
	[5] -1	0	0xfe8f8000 - 0xfe8fbfff (0x4000) MX[B]
	[6] -1	0	0xfe8ffc00 - 0xfe8fffff (0x400) MX[B]
	[7] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B](B)
	[8] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[11] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[12] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[14] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[16] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[17] -1	0	0x00009480 - 0x0000948f (0x10) IX[B]
	[18] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[19] -1	0	0x00009880 - 0x00009887 (0x8) IX[B]
	[20] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[22] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[23] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[24] -1	0	0x0000a480 - 0x0000a48f (0x10) IX[B]
	[25] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[26] -1	0	0x0000a880 - 0x0000a887 (0x8) IX[B]
	[27] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[28] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[29] -1	0	0x0000b080 - 0x0000b09f (0x20) IX[B]
	[30] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[31] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[32] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[33] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[34] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[35] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeafffff (0x400) MX[B]
	[6] -1	0	0xfe9ec000 - 0xfe9effff (0x4000) MX[B]
	[7] -1	0	0xfe8ff400 - 0xfe8ff4ff (0x100) MX[B]
	[8] -1	0	0xfe8ff800 - 0xfe8ffbff (0x400) MX[B]
	[9] -1	0	0xfe8f8000 - 0xfe8fbfff (0x4000) MX[B]
	[10] -1	0	0xfe8ffc00 - 0xfe8fffff (0x400) MX[B]
	[11] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B](B)
	[12] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[18] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[20] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[22] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[23] -1	0	0x00009480 - 0x0000948f (0x10) IX[B]
	[24] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[25] -1	0	0x00009880 - 0x00009887 (0x8) IX[B]
	[26] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[27] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[28] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[29] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[30] -1	0	0x0000a480 - 0x0000a48f (0x10) IX[B]
	[31] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[32] -1	0	0x0000a880 - 0x0000a887 (0x8) IX[B]
	[33] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[34] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[35] -1	0	0x0000b080 - 0x0000b09f (0x20) IX[B]
	[36] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[37] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[38] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[39] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[40] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[41] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01:00:0
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeafffff (0x400) MX[B]
	[6] -1	0	0xfe9ec000 - 0xfe9effff (0x4000) MX[B]
	[7] -1	0	0xfe8ff400 - 0xfe8ff4ff (0x100) MX[B]
	[8] -1	0	0xfe8ff800 - 0xfe8ffbff (0x400) MX[B]
	[9] -1	0	0xfe8f8000 - 0xfe8fbfff (0x4000) MX[B]
	[10] -1	0	0xfe8ffc00 - 0xfe8fffff (0x400) MX[B]
	[11] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B](B)
	[12] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[18] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[20] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[22] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[23] -1	0	0x00009480 - 0x0000948f (0x10) IX[B]
	[24] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[25] -1	0	0x00009880 - 0x00009887 (0x8) IX[B]
	[26] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[27] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[28] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[29] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[30] -1	0	0x0000a480 - 0x0000a48f (0x10) IX[B]
	[31] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[32] -1	0	0x0000a880 - 0x0000a887 (0x8) IX[B]
	[33] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[34] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[35] -1	0	0x0000b080 - 0x0000b09f (0x20) IX[B]
	[36] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[37] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[38] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[39] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[40] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[41] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeafffff (0x400) MX[B]
	[6] -1	0	0xfe9ec000 - 0xfe9effff (0x4000) MX[B]
	[7] -1	0	0xfe8ff400 - 0xfe8ff4ff (0x100) MX[B]
	[8] -1	0	0xfe8ff800 - 0xfe8ffbff (0x400) MX[B]
	[9] -1	0	0xfe8f8000 - 0xfe8fbfff (0x4000) MX[B]
	[10] -1	0	0xfe8ffc00 - 0xfe8fffff (0x400) MX[B]
	[11] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B](B)
	[12] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[21] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[23] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[25] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[26] -1	0	0x00009480 - 0x0000948f (0x10) IX[B]
	[27] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[28] -1	0	0x00009880 - 0x00009887 (0x8) IX[B]
	[29] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[30] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[31] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[32] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[33] -1	0	0x0000a480 - 0x0000a48f (0x10) IX[B]
	[34] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[35] -1	0	0x0000a880 - 0x0000a887 (0x8) IX[B]
	[36] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[37] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[38] -1	0	0x0000b080 - 0x0000b09f (0x20) IX[B]
	[39] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[40] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[41] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[42] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[43] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[44] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[45] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[46] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
(II) VESA(0): VESA VBE OEM Software Rev: 10.73
(II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) VESA(0): VESA VBE OEM Product: A
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(**) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: VSC  Model: 111e  Serial#: 16843009
(II) VESA(0): Year: 2007  Week: 35
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) VESA(0): Signal levels configurable
(II) VESA(0): Sync:  Separate
(II) VESA(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: Off; RGB/Color Display
(II) VESA(0): Default color space is primary color space
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.644 redY: 0.328   greenX: 0.290 greenY: 0.614
(II) VESA(0): blueX: 0.142 blueY: 0.079   whiteX: 0.310 whiteY: 0.340
(II) VESA(0): Supported VESA Video Modes:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@67Hz
(II) VESA(0): 640x480@72Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@56Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@72Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 832x624@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@70Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1280x1024@75Hz
(II) VESA(0): 1152x870@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported Future Video Modes:
(II) VESA(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) VESA(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) VESA(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) VESA(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) VESA(0): #4: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) VESA(0): #5: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) VESA(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) VESA(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) VESA(0): Serial No: Q87073532148
(II) VESA(0): Ranges: V min: 50  V max: 85 Hz, H min: 30  H max: 82 kHz, PixClock max 140 MHz
(II) VESA(0): Monitor name: VA903 SERIES
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff005a631e1101010101
(II) VESA(0): 	2311010318261e782ec554a4544a9d24
(II) VESA(0): 	144f57bfef8081808140714f61594559
(II) VESA(0): 	315901010101302a009851002a403070
(II) VESA(0): 	1300782d1100001e000000ff00513837
(II) VESA(0): 	3037333533323134380a000000fd0032
(II) VESA(0): 	551e520e000a202020202020000000fc
(II) VESA(0): 	005641393033205345524945530a00b2
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) VESA(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) VESA(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) VESA(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) VESA(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) VESA(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) VESA(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) VESA(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) VESA(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) VESA(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) VESA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) VESA(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) VESA(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) VESA(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) VESA(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) VESA(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) VESA(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) VESA(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) VESA(0): Modeline "1024x768"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
(II) VESA(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(II) VESA(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(II) VESA(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 101 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 50
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 50
	LinNumberOfImagePages: 50
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 103 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 832
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 832
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 105 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 18
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 18
	LinNumberOfImagePages: 18
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 107 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 111 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 24
	LinNumberOfImagePages: 24
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 114 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 16
	LinNumberOfImagePages: 16
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 117 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 11a (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 10e (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 127
	LinNumberOfImagePages: 127
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 120 (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 193 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 127
	LinNumberOfImagePages: 127
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 195 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 84
	LinNumberOfImagePages: 84
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 196 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 50
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 50
	LinNumberOfImagePages: 50
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1b3 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 512
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 512
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1b5 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 1024
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 35
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 35
	LinNumberOfImagePages: 35
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 1b6 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 2048
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 18
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 18
	LinNumberOfImagePages: 18
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1c3 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1c5 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 35
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 35
	LinNumberOfImagePages: 35
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 1c6 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 17
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 17
	LinNumberOfImagePages: 17
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 183 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 185 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 186 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 133 (720x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 768
	XResolution: 720
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 50
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 768
	BnkNumberOfImagePages: 50
	LinNumberOfImagePages: 50
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 135 (720x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 1472
	XResolution: 720
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 27
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1472
	BnkNumberOfImagePages: 27
	LinNumberOfImagePages: 27
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 136 (720x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 2944
	XResolution: 720
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 13
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2944
	BnkNumberOfImagePages: 13
	LinNumberOfImagePages: 13
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 153 (1152x864)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 1152
	XResolution: 1152
	YResolution: 864
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1152
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 155 (1152x864)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 2304
	XResolution: 1152
	YResolution: 864
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2304
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 156 (1152x864)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 4608
	XResolution: 1152
	YResolution: 864
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 4608
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 163 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 165 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 166 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 121 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 12
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 12
	LinNumberOfImagePages: 12
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 122 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 123 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 124 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 143 (1400x1050)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 1408
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1408
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 145 (1400x1050)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 2816
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2816
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 146 (1400x1050)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 5632
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 5632
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 173 (1600x1200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 175 (1600x1200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 176 (1600x1200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 6400
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 6400
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 183 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 185 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 186 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1d3 (1856x1392)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 1856
	XResolution: 1856
	YResolution: 1392
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1856
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1d5 (1856x1392)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 3712
	XResolution: 1856
	YResolution: 1392
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 3712
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 1d6 (1856x1392)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 7424
	XResolution: 1856
	YResolution: 1392
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 7424
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1e3 (1920x1440)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 1920
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1920
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
Mode: 1e5 (1920x1440)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 3840
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 3840
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000
*Mode: 1e6 (1920x1440)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00050cd
	BytesPerScanline: 7680
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 7680
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 400000000

(II) VESA(0): Total Memory: 256 64KB banks (16384kB)
(II) VESA(0): VA903 SERIES: Using hsync range of 30.00-82.00 kHz
(II) VESA(0): VA903 SERIES: Using vrefresh range of 50.00-85.00 Hz
(II) VESA(0): Not using mode "1280x960" (no mode of this name)
(II) VESA(0): Not using mode "832x624" (no mode of this name)
(II) VESA(0): Not using built-in mode "1920x1440" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1856x1392" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1600x1200" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1400x1050" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
(II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
(**) VESA(0): *Built-in mode "1280x1024"
(**) VESA(0): *Built-in mode "1152x864"
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "720x400"
(**) VESA(0): *Built-in mode "640x480"
(**) VESA(0):  Built-in mode "1280x1024"
(**) VESA(0): Display dimensions: (380, 300) mm
(**) VESA(0): DPI set to (85, 86)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1280x1024" (166)
(II) VESA(0): Attempting to use 85Hz refresh for mode "1152x864" (156)
(II) VESA(0): Attempting to use 85Hz refresh for mode "1024x768" (123)
(II) VESA(0): Attempting to use 85Hz refresh for mode "800x600" (122)
(II) VESA(0): Attempting to use 85Hz refresh for mode "720x400" (136)
(II) VESA(0): Attempting to use 85Hz refresh for mode "640x480" (121)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1280x1024" (124)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeafffff (0x400) MX[B]
	[6] -1	0	0xfe9ec000 - 0xfe9effff (0x4000) MX[B]
	[7] -1	0	0xfe8ff400 - 0xfe8ff4ff (0x100) MX[B]
	[8] -1	0	0xfe8ff800 - 0xfe8ffbff (0x400) MX[B]
	[9] -1	0	0xfe8f8000 - 0xfe8fbfff (0x4000) MX[B]
	[10] -1	0	0xfe8ffc00 - 0xfe8fffff (0x400) MX[B]
	[11] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B](B)
	[12] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[21] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[23] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[25] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[26] -1	0	0x00009480 - 0x0000948f (0x10) IX[B]
	[27] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[28] -1	0	0x00009880 - 0x00009887 (0x8) IX[B]
	[29] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[30] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[31] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[32] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[33] -1	0	0x0000a480 - 0x0000a48f (0x10) IX[B]
	[34] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[35] -1	0	0x0000a880 - 0x0000a887 (0x8) IX[B]
	[36] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[37] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[38] -1	0	0x0000b080 - 0x0000b09f (0x20) IX[B]
	[39] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[40] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[41] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[42] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[43] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[44] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[45] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[46] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
(II) VESA(0): VESA VBE OEM Software Rev: 10.73
(II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) VESA(0): VESA VBE OEM Product: A
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(==) VESA(0): Write-combining range (0xd0000000,0x1000000)
(II) VESA(0): virtual address = 0xb6a0e000,
	physical address = 0xd0000000, size = 16777216
(II) VESA(0): VBESetVBEMode failed...Tried again without customized values.
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
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
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
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
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetGrabKeysState - disabled
SetGrabKeysState - enabled

---

### Post by rockinlinux on 2008-03-07
got it all working using envy :)

---

### Post by kellemes on 2008-03-07
> **rockinlinux said:**
> got it all working using envy :)

Serious? Man, that's good news.. well done.

---

