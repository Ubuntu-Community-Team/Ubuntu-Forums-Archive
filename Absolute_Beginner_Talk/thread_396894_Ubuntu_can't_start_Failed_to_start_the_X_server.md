---
title: "Ubuntu can't start: Failed to start the X server"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-03-30
Hi,
yesterday I was playing around with x server settings, but today I have boot up the linux I got the message: "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem? Yes, No.

If pressing Yes:
A lot of data are displayed. At the bottom there is VESA: No matching modes. Screen foud, but none have a usable configuration. Fatal server error: no screens found.

After pressing OK (the only option), I get login to command mode. I can login, but no graphical interface.

Is there any way to undo all settings I have done yesterday? So how to start Ubuntu in graphic mode? Any help is appreciated?

Thanks,
Abcuser

My system:
ubuntu linux 6.10 desktop edition on x86 32-bit Intel

---

### Post by nixclusive on 2007-03-30
oh...k now you are in for some text mode text editing. So exactly what was it you've changed yesterday?

---

### Post by spin2cool on 2007-03-30
If you were smart, you made a backup copy of your xorg.conf file before mucking around with it  (found in /etc/X11/xorg.conf).  If you didn't, you'll want to start from scratch.  Boot into a command line and run

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by zorkerz on 2007-03-30
If there as a backup or you know what you changed you can type 
```
cd /etc/X11/
ls
```
this will list the files there so you know the name of the backup

to edit xorg type 
```
sudo nano /etc/X11/xorg.conf
```

copy command is cp

---

### Post by abcuser on 2007-03-30
Hi,
thanks for help. I tried running sudo dpkg-reconfigure xserver-xorg but I just don't know what I have changed - there was so many things I was trying (multiple times), but I have realized that the changes have taken into effect after reboot.

I have checked the: sudo nano /etc/X11/xorg.conf but there is too many options. Just don't know what I have changed.

BTW, I have installed IBM DB2 database few days ago on this computer and as I see it is still working, but x-window would help... :)

Is there any way to say something like "autoconfigure", just like Linux does when installing? Is there any settings to have minimum compatibility of hardware. Something like Windows has when booting (after installation) for the first time?

Thanks,
Abcuser

---

### Post by zorkerz on 2007-03-30
As far as i Know this is the closes to auto configure as it gets
```
sodu dpkg-reconfigure xserver-xorg
```
the simple method should not ask you more than you filled out when you installed

If this does not work you could post the errors or the whole log of errors when x crashes. It should tell you where it is stored in the x crash report.

---

### Post by abcuser on 2007-03-30
zorkerz, the above command starts text interface to manualy set up configs. The same window I have mis-configure yesterday.

Ok, I have mounted the floppy and the bellow is log file from /var/logs/Xorg.0.log (log file that linux reported at boot).

```


X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux igortest 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 30 08:17:19 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2560 card ffff,ffff rev 01 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2562 card 1014,0267 rev 01 class 03,00,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24c2 card 1014,0267 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1014,0267 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1014,0267 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1014,0267 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 81 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 1014,0267 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 1014,0267 rev 01 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1014,0267 rev 01 class 04,01,00 hdr 00
(II) PCI: 02:08:0: chip 8086,1039 card 1014,0267 rev 81 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xc0100000 - 0xc01fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device rev 1, Mem @ 0x88000000/27, 0x80000000/19
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xdfffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xc0100000 - 0xc0100fff (0x1000) MX[B]
	[1] -1	0	0xc0080800 - 0xc00808ff (0x100) MX[B]
	[2] -1	0	0xc0080c00 - 0xc0080dff (0x200) MX[B]
	[3] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[4] -1	0	0xc0080000 - 0xc00803ff (0x400) MX[B]
	[5] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[6] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B](B)
	[7] -1	0	0x88000000 - 0x8fffffff (0x8000000) MX[B](B)
	[8] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[9] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[10] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[11] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[12] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[13] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[14] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[15] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc0100000 - 0xc0100fff (0x1000) MX[B]
	[1] -1	0	0xc0080800 - 0xc00808ff (0x100) MX[B]
	[2] -1	0	0xc0080c00 - 0xc0080dff (0x200) MX[B]
	[3] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[4] -1	0	0xc0080000 - 0xc00803ff (0x400) MX[B]
	[5] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[6] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B](B)
	[7] -1	0	0x88000000 - 0x8fffffff (0x8000000) MX[B](B)
	[8] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[9] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[10] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[11] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[12] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[13] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[14] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[15] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
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
	[4] -1	0	0xc0100000 - 0xc0100fff (0x1000) MX[B]
	[5] -1	0	0xc0080800 - 0xc00808ff (0x100) MX[B]
	[6] -1	0	0xc0080c00 - 0xc0080dff (0x200) MX[B]
	[7] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[8] -1	0	0xc0080000 - 0xc00803ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B](B)
	[11] -1	0	0x88000000 - 0x8fffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[15] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[16] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[17] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[18] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[19] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[20] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[21] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "vga"
(II) Loading /usr/lib/xorg/modules/drivers/vga_drv.so
(II) Module vga: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 4.1.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) VGA: Generic VGA driver (version 4.1) for chipsets: generic
(II) Primary Device is: PCI 00:02:0
(--) Chipset generic found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0100000 - 0xc0100fff (0x1000) MX[B]
	[5] -1	0	0xc0080800 - 0xc00808ff (0x100) MX[B]
	[6] -1	0	0xc0080c00 - 0xc0080dff (0x200) MX[B]
	[7] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[8] -1	0	0xc0080000 - 0xc00803ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B](B)
	[11] -1	0	0x88000000 - 0x8fffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[15] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[16] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[17] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[18] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[19] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[20] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[21] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0100000 - 0xc0100fff (0x1000) MX[B]
	[5] -1	0	0xc0080800 - 0xc00808ff (0x100) MX[B]
	[6] -1	0	0xc0080c00 - 0xc0080dff (0x200) MX[B]
	[7] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[8] -1	0	0xc0080000 - 0xc00803ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0x80000000 - 0x8007ffff (0x80000) MX[B](B)
	[11] -1	0	0x88000000 - 0x8fffffff (0x8000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[18] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[19] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[20] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[21] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[22] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[23] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[24] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VGA(0): initializing int10.
(WW) VGA(0): Bad V_BIOS checksum
(II) VGA(0): Primary V_BIOS segment is: 0xc000
(EE) VGA(0): Driver can't support depth 24
(II) UnloadModule: "vga"
(II) UnloadModule: "int10"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

Any idea? Can someone check there conf file to see how it is configured?
Thanks,
Abcuser

---

### Post by freebird54 on 2007-03-30
Looks like it died on the load of the video driver.  It is easiest to rebuild to xorg.conf file by using the command:
```

dpkg-reconfigure xserver.xorg
```

This will give a DOS type 'graphic' interface.  Movement is by <tab> key between 'groups',  <arrow> keys within groups, <space> to select or unselect items, and <enter> to confirm OK or complete an entry.

If you don't KNOW that you need to change something- leave the defaults alone - they usually make sense.  Select the video drive that you KNOW works - vesa should function till you get going again if you aren't sure.  Pick only resolutions for your monitor that you KNOW work.

When it has completed, a new xorg.conf file will have been created that should be good enough to do for now.

A reboot should see you in action again.  (not required, but It is easier)

---

### Post by zorkerz on 2007-03-30
> (ee) VGA(0): Driver can't support depth 24
(ee) Screen(s) found, but none hove usable configuration.So these are the two errors you encountered. This is likely caused by having your monitor or graphics card set up improperly. What graphics card do you have?

You could try editing xorg.conf with the command above and going to the screen section and changing the default depth from 24 to one of the depths set up below it in the screen subsection. However if you are not using the right driver this would not likely work.

all of the warnings (ww) worrie me but if they are not errors (ee) i believe you can get through fine.  especially the last warning VGA(0): bad V_BIOS checksum
this makes me thing your bios could be corrupted somehow. but this is most likely just my imagination as if something was wrong with your bios you would not get this far in the boot process.

upd: freebird54 is right the command is the easiest way and usually the defaults work well.

---

### Post by freebird54 on 2007-03-30
I'm assuming the BIOS refers to the video card BIOS - but we won't know for a while... :)

---

### Post by zorkerz on 2007-03-30
Oh that would make sense.

---

### Post by abcuser on 2007-03-30
Hi,
I have tried to lower the number of video card. Reboot and now one more "little" problem:
executing command: dpkg-reconfigure xserver.xorg reports message:
Package'xserver.xorg' is not installed and no info is available.

Any idea?


BTW, is there any "repair" option like in Windows? I have Ubuntu Live CD so if I could just use "repair"? Any idea?

Thanks,
Abcuser

---

### Post by zorkerz on 2007-03-30
What exactly did you try to do?

---

### Post by abcuser on 2007-03-30
Hi,
I went into recovery mode and it looks like I have made a bigger mess.

Is there any "repair" option in Ubuntu Live CD?

Thanks,
Abcuser

---

### Post by zorkerz on 2007-03-30
Not to my knowledge although i could be very wrong. 

What did you do in recovery mode. I am trying to think of what could have caused you to get that error.

---

### Post by freebird54 on 2007-03-30
I am not sure of the package name, so I can't help you just yet.  There is bound to be a 'sudo apt-get <packagename> that will work - so hang on till an expert gets to you!

Unless, of course, you have everything you have created backed up somewhere - or haven't made any user files yet - then a re-install will work too. 

Wait a while - and see if anyone knows - or I find it for you... :)

Good luck.

---

### Post by zorkerz on 2007-03-30
This is an old link but it makes me believe the package is just xserver-xorg [http://ubuntuforums.org/showthread.php?p=2104537](http://ubuntuforums.org/showthread.php?p=2104537)
so if you enter
```
sudo aptitude install xserver-xorg
```
you can replace aptitude with apt-get also although i have been told aptitude has some benefits over apt-get

---

### Post by abcuser on 2007-03-30
Hi,
I went throught xserver-xorg dos like interface and trying to change vga to vesa. After that I reboot. Linux has found out that there was no successfull start (or somthing) and automatically start disk checking. I was inpatient so I press restart button. So...

I have decited to install Ubuntu again. I have just begain reinstalling. I am just having fun to know the differences between Ubuntu Linux and Windows. I am an computer jurnalist and I am writting an article about how much Linux has in progress by some years. I have been working on Windows more then 10 years and I would just like to get the same functionalities on Linux. I think Ubuntu is the closes to this idea. I was just to happy and trying to much with to less knowleadge.

BTW, is there any good tool to backup the whole disk to another. So to make backup. On Windows I use Symantec Ghost. Any such tool on Linux?

Thanks,
Abcuser

---

### Post by abcuser on 2007-03-30
Hi,
sorry I have just began reinstalling before read your posts, Windows habit :)
Thanks for help,
Abcuser

---

### Post by freebird54 on 2007-03-30
Afraid I can't even remember the name of the one I used.  It's a freeware I found on ZDNet or TechRepublic....

There are a *LOT* of Google hits on this.  Many of them seem to be OS agnostic (running under FreeDOS or the like) - and just image by partition off a boot floppy.

I also saw a use of 'dd' that apparently does similar things - but I'm too much of a n00bie this time around to be sure of that.

Pretty sure the re-install was an over-reaction - just put the xserver-xorg package back on - but at least a re-install is something we all know how to do if we got this far at all!

The message above had the command to re-install the xserver - and I found a list of dependencies in the Synaptic Package Manager - it should have worked....

---

### Post by freebird54 on 2007-03-30
Darn - and I was so careful NOT to say it was a Windows habit!  (that's where I got it, anyway)

:D

---

### Post by zorkerz on 2007-03-30
a fresh install is always nice anyways  When i back up my home partition i use this command from the home directory

```
find . -depth -print0 | sudo cpio --null --sparse -pvd "/backup/dir"
```"/backup/dir" is the directory you would like the backup to be stored in. I use an external hardrive

i don't pretend to have any idea what the parts of this command do but it works for me unlike any other method i have tried

---

### Post by freebird54 on 2007-03-30
At least we can go  **info cpio** in a terminal and figure out what's going on!

---

### Post by abcuser on 2007-03-30
freebird54, zorkerz's thanks for help. I have reinstall Ubuntu and all of the needed software - so no more then two hours of work. Fist time I have installed linux and all software I needed at lest I week. So it is not so difficult to leart it. Btw, I was just wondering if xserver would be up till now. ;)

So problem solved. No need on this topic. I have learned the lesson - don't change system settings just for having fun. ;)

---

### Post by zorkerz on 2007-03-30
Or have a backup so when you do break things you can just revert.
This [bullet-proof-x]("https://blueprints.launchpad.net/ubuntu/+spec/bullet-proof-x") feature on launchpad for feisty+1 is particularly exciting for me, it should help prevent x from breaking as often. 

Great to here things are up and running again and thanks for checking in after the storm settled.

---

