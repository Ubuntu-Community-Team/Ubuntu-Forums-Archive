---
title: "Edgy Problems"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by mtgrocks04 on 2006-10-27
I upgraded from 6.06 to 6.10 and when I boot I see the kubuntu splash screen and then it disapears and I just get black screen with a blinking white cursor. I remember reading somewhere someone had to install X??? Any help would be appreciated. Thanks in advance for any help.

---

### Post by Gannin on 2006-10-28
If you wait for a while, does it eventually give you an error message?

---

### Post by mtgrocks04 on 2006-10-28
I just tried it...it went to the black screen and eventually it said ubuntu 6.10 greg-laptop tty1. and then greg-laptop login:

I enter my login and then it just says greg@greg-laptop so I dont know if its not loading X or I ran sudo apt-get -f dist-upgrade and it still doesnt work. Any thoughts?

---

### Post by Gannin on 2006-10-28
Do you have an Xorg.0.log file in your /var/log directory?  If you do, take a look at it and see if there are any error messages listed in it.

---

### Post by mtgrocks04 on 2006-10-28
I don't know how to get to /var/log to see if there are errors. I still get the blinking cursor for  a long time followed by what I said before.

---

### Post by Gannin on 2006-10-28
After you login to your system on the command line, type:

cat /var/log/Xorg.0.log

And then after it's all displayed on the screen, if you need to scroll through it, hold down shift and press page up and page down.

---

### Post by nevin on 2006-10-30
i am having similar problems.
i upgraded from 6.04, if you can call it upgrading.  (regular ubuntu with gnome)
it loads all the way to the login screen, and then when i try to login, it pretends like its going to work, and then stops, and crashes to that same blank screen... but i have never gotten a login thing on that screen... i press ctrl+alt+backspace and that takes me back to the login screen, where i can start up the failsafe terminal, but i dont know what to do, i tried the apt-get dist-upgrade again, and i tried apt-get update, and i thought it might be a problem with gnome, so i tried, apt-get install gnome, but nothing ive tried seem to fix it.  i think it must be something like what you've been getting... something having to do with X.  ill try to find that file and see whats up, but im not that advance in the linux use, so i dont know exactly what im looking for.

but if anyone has better insight, im sure it would help us, and probably others who have this same problem.

nevin

---

### Post by nevin on 2006-10-30
i looked up my /var/log/Xorg.0.log file, and it had a few errorish problems at the very bottom of it... i looked throught the whole thing, but didnt see any others...

it said:

"Could not init font path element /usr/share/fonts/X11/TTF/ , removing from list!
Could not init font path element /usr/share/fonts/X11/OTF/ , removing from list!
Could not init font path element /usr/share/fonts/X11/C1D/ , removing from list!"


I tried to go to those directories, but they do not exist in the /usr/share/fonts/X11 directory.  i dont know exactly what to do from here.

nevin

---

### Post by sirlancelot on 2006-10-30
I'm having the same problem, running *upgraded from dapper* Kubuntu 6.10.

I found that after getting the blinking cursor, loggging in, and restarting kdm via ```
/etc/init.d/kdm restart
``` I was able to get the normal login screen and run KDE.

Here's what my Xorg.0.log looks like. I've deleted some irrevelent font error infos at the bottom. However, there's some errors I don't understand.```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux fiuze1 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 29 08:06:59 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "VA712-2SERIE"
(**) |   |-->Device "NVIDIA Corporation NV34 [GeForce FX 5200]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/usr/share/fonts/X11/misc,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
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
(II) PCI: 00:00:0: chip 1106,3189 card 1043,807f rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b168 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0b:0: chip 100b,0020 card 1385,f311 rev 00 class 02,00,00 hdr 00
(II) PCI: 00:0f:0: chip 1102,0004 card 1102,0051 rev 03 class 04,01,00 hdr 80
(II) PCI: 00:0f:1: chip 1102,7003 card 1102,0040 rev 03 class 09,80,00 hdr 80
(II) PCI: 00:0f:2: chip 1102,4001 card 1102,0010 rev 00 class 0c,00,10 hdr 80
(II) PCI: 00:10:0: chip 1106,3038 card 1043,80a1 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1043,80a1 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1043,80a1 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3104 card 1043,80a1 rev 82 class 0c,03,20 hdr 00
(II) PCI: 00:11:0: chip 1106,3177 card 1043,80a1 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1043,80a1 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1043,80a1 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1043,80a1 rev 74 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0322 card 1462,9110 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe6000000 - 0xe7dfffff (0x1e00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe7f00000 - 0xefffffff (0x8100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xe6000000/24, 0xe8000000/27, BIOS @ 0xe7fe0000/17
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
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe3800000 - 0xe38000ff (0x100) MX[B]
	[1] -1	0	0xe4000000 - 0xe40000ff (0x100) MX[B]
	[2] -1	0	0xe4800000 - 0xe4803fff (0x4000) MX[B]
	[3] -1	0	0xe5000000 - 0xe50007ff (0x800) MX[B]
	[4] -1	0	0xe5800000 - 0xe5800fff (0x1000) MX[B]
	[5] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[6] -1	0	0xe7fe0000 - 0xe7ffffff (0x20000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[10] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[11] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[12] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[13] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[14] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe3800000 - 0xe38000ff (0x100) MX[B]
	[1] -1	0	0xe4000000 - 0xe40000ff (0x100) MX[B]
	[2] -1	0	0xe4800000 - 0xe4803fff (0x4000) MX[B]
	[3] -1	0	0xe5000000 - 0xe50007ff (0x800) MX[B]
	[4] -1	0	0xe5800000 - 0xe5800fff (0x1000) MX[B]
	[5] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[6] -1	0	0xe7fe0000 - 0xe7ffffff (0x20000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[10] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[11] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[12] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[13] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[14] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
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
	[4] -1	0	0xe3800000 - 0xe38000ff (0x100) MX[B]
	[5] -1	0	0xe4000000 - 0xe40000ff (0x100) MX[B]
	[6] -1	0	0xe4800000 - 0xe4803fff (0x4000) MX[B]
	[7] -1	0	0xe5000000 - 0xe50007ff (0x800) MX[B]
	[8] -1	0	0xe5800000 - 0xe5800fff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xe7fe0000 - 0xe7ffffff (0x20000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[17] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[18] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[20] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
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
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9625
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9625
	Module class: X.Org Video Driver
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
(II) NVIDIA dlloader X Driver  1.0-9625  Thu Sep 14 15:35:06 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3800000 - 0xe38000ff (0x100) MX[B]
	[5] -1	0	0xe4000000 - 0xe40000ff (0x100) MX[B]
	[6] -1	0	0xe4800000 - 0xe4803fff (0x4000) MX[B]
	[7] -1	0	0xe5000000 - 0xe50007ff (0x800) MX[B]
	[8] -1	0	0xe5800000 - 0xe5800fff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xe7fe0000 - 0xe7ffffff (0x20000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[17] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[18] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[20] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3800000 - 0xe38000ff (0x100) MX[B]
	[5] -1	0	0xe4000000 - 0xe40000ff (0x100) MX[B]
	[6] -1	0	0xe4800000 - 0xe4803fff (0x4000) MX[B]
	[7] -1	0	0xe5000000 - 0xe50007ff (0x800) MX[B]
	[8] -1	0	0xe5800000 - 0xe5800fff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xe7fe0000 - 0xe7ffffff (0x20000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[20] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[21] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[22] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[25] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.22.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     ViewSonic VA712-2SERIES (CRT-0)
(--) NVIDIA(0): ViewSonic VA712-2SERIES (CRT-0): 350.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1600x1200"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
	[1] 0	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe3800000 - 0xe38000ff (0x100) MX[B]
	[7] -1	0	0xe4000000 - 0xe40000ff (0x100) MX[B]
	[8] -1	0	0xe4800000 - 0xe4803fff (0x4000) MX[B]
	[9] -1	0	0xe5000000 - 0xe50007ff (0x800) MX[B]
	[10] -1	0	0xe5800000 - 0xe5800fff (0x1000) MX[B]
	[11] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[12] -1	0	0xe7fe0000 - 0xe7ffffff (0x20000) MX[B](B)
	[13] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[14] -1	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[22] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[24] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[25] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[26] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[27] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[28] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
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
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
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
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc104)+us" };
    xkb_geometry             { include "pc(pc104)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
    xkb_types                { include "%" };
    xkb_compatibility        { include "%" };
    xkb_symbols              { include "%" };
    xkb_geometry             { include "%" };
(EE) Error loading keymap /var/lib/xkb/server-0.xkm
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
(II) 3rd Button detected: disabling emulate3Button
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
SetClientVersion: 0 9
(II) 3rd Button detected: disabling emulate3Button
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
```Any ideas?

---

### Post by Gannin on 2006-10-30
I don't see any errors in there that should be causing any problems.  The font errors and the Wacom errors shouldn't be causing the X server to crash or not start.  Nevin, what video card and driver are you using?  And sirlancelot, have you tried using the current stable nVidia drivers instead of the beta drivers to see if things work any differently?

---

### Post by MarkoSK on 2006-10-30
i remember when i upgraded from dapper to edgy i it didn't start X automaticly and kept geting me to conzole..

all i did was:

apt-get --reinstall install xserver-xorg

and:

dokg-reconfigure xserver-xorg

and after that everything was back to normal...so you could try doing this too...

---

### Post by nevin on 2006-10-30
i have an ati x300 mobile  (its a laptop) and i have the fglrx or what not driver.  i had been using compiz, so i had to get that driver instead of the mesa driver or whatever it was before.

i guess i'll try the reinstall thing like this guy has just posted...

---

### Post by nevin on 2006-10-30
i tried to reinstall xserver-xorg, but that didnt help, i tried to update my xorg.conf file, but that just messed up my screen, and i tried using enlightenment, and it work for a second, but then it crashed... i tried to install kde to see if i could use that, but i couldnt get it install (something about some dependency that wouldnt install).  

still doesnt load gnome...
i am now wishing i had not have upgraded.

---

### Post by Gannin on 2006-10-30
Did you only try to update your xorg.conf file, or did you use the actual dpkg-reconfigure xserver-xorg command?

---

### Post by nevin on 2006-10-30
i did the dpkg-reconfigure.
but everytime ive gone through this, i mess up the xorg.conf file...

---

### Post by sirlancelot on 2006-10-31
> **Gannin said:**
> And sirlancelot, have you tried using the current stable nVidia drivers instead of the beta drivers to see if things work any differently?Are the non-beta nvidia drivers in the universe repositories?

---

### Post by Gannin on 2006-10-31
It's always a good idea to make a backup copy of your xorg.conf file before you do anything that may affect it, just in case.

As for the nVidia drivers, I'm not sure what's in the repositories, as I always get and install the drivers from nVidia's website.

---

### Post by dinub1 on 2006-10-31
This is in response to the initial poster. I am having similar problems. It goes to a blank blinking cursor screen, after the initial screen shows various driverds being loaded OK< etc...
I upgraded from Dapper 6.06 to 6.10 using Kubuntu. However I have all 3 GUI's including Gnome and Xface. I apparently stopped the instl in the middle and it did not finish. It would report that Ubuntu may not run properly. Upon restart I cannot go into the graphic mode. In text I enter my login and password it logs into a text promt fine, and doing startx it gives me errors. I assume Xorg has not been installed properly

Anyweay.. I tried couple of options until it reported that dpkg did not configure properly cause routine was stopped in the middle. OS sugests to try: sudo dpkg --configure -a

I indeed tried it and it is updating/configuring right now. I guess this will fix it. Will report later.

---

