---
title: "Please help!!!! x-server crached"
date: 2010-05-20
forum: Apple Hardware Users
---

### Post by nmvictor on 2010-05-20
My x-server crashed, yes after trying to tweak my xorg.conf so i would get my ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02) graphics card to achieve a better graphics perfomance like the one i used to see in mac(),by the way I am running karmic in an IBook g4/800 with the above mentioned graphics card. My x-server gave up and this time it dint leave me any meaning full message to help me resolve the issue, so i am posting my /var/log/Xorg.0.log for help from those who have a better experience with X because for me , I can't seem to understand the cause of the error.
Here's my /var/log/Xorg.0.log:
```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.31-20-powerpc64-smp ppc Ubuntu
Current Operating System: Linux nmvictors-linuxbox 2.6.31-21-powerpc #59-Ubuntu Wed Mar 24 07:29:48 UTC 2010 ppc
Kernel command line: root=/dev/hda3 ro quiet splash 
Build Date: 07 May 2010  10:24:17AM
xorg-server 2:1.6.4-2ubuntu4.3 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed May 19 04:41:28 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(==) No device specified for screen "Default Screen".
	Using the first device section listed.
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) Option "AIGLX" "true"
(==) Automatically adding devices
(==) Automatically enabling devices
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
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Generic Keyboard
(WW) Disabling Configured Mouse
(II) Loader magic: 0x3e90
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:0:16:0) 1002:4c46:1002:4c46 ATI Technologies Inc Rage Mobility M3 AGP 2x rev 2, Mem @ 0x94000000/67108864, 0x90000000/16384, I/O @ 0x00000400/256, BIOS @ 0x????????/131072
(II) Open APM successful
(II) System resource ranges:
	[0] -1	2	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	2	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	2	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	2	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	2	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	2	0x00000000 - 0x00000000 (0x1) IX[B]
	[14] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded by default.
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(**) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 6.12.99
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "r128"
(II) Loading /usr/lib/xorg/modules/drivers//r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 6.8.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) v4l driver for Video4Linux
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) Primary Device is: PCI 00@00:10:0
(WW) Falling back to old probe method for v4l
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	2	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	2	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	2	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	2	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	2	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	2	0x00000000 - 0x00000000 (0x1) IX[B]
	[14] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	2	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	2	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	2	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	2	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	2	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	2	0x00000000 - 0x00000000 (0x1) IX[B]
	[17] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[21] 0	0	0xf00003b0 - 0xf00003bb (0xc) IS[B]
	[22] 0	0	0xf00003c0 - 0xf00003df (0x20) IS[B]
(II) R128(0): PCI bus 0 card 16 func 0
(**) R128(0): Depth 16, (--) framebuffer bpp 16
(II) R128(0): Pixel depth = 16 bits stored in 2 bytes (16 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(**) R128(0): Option "accel" "true"
(**) R128(0): Option "CCEusecTimeout" "100000"
(**) R128(0): Option "AGPMode" "4"
(**) R128(0): Option "EnablePageFlip" "true"
(**) R128(0): Option "UseFBDev" "false"
(II) R128(0): VGAAccess option set to FALSE, VGA module load skipped
(==) R128(0): RGB weight 565
(II) R128(0): Using 6 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) R128(0): initializing int10

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x50) [0x101075f0]
1: /usr/bin/X(xf86SigHandler+0x70) [0x1008d190]
2: [0x100364]
3: /usr/lib/xorg/modules//libint10.so(xf86ExtendedInitInt10+0x380) [0xf7bc1e0]
4: /usr/lib/xorg/modules//libint10.so(xf86InitInt10+0x28) [0xf7b7ba8]
5: /usr/lib/xorg/modules/drivers//r128_drv.so(R128PreInit+0x5d0) [0xf6c8930]
6: /usr/bin/X(InitOutput+0x5bc) [0x1007194c]
7: /usr/bin/X(main+0x224) [0x10028344]
8: /lib/libc.so.6 [0xfa6c59c]
9: /lib/libc.so.6 [0xfa6c760]
Saw signal 7.  Server aborting.
 ddxSigGiveUp: Closing log
```

and the /etc/X11/xorg.conf reads as follows:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier "Configured Monitor"
	HorizSync 58-62
	VertRefresh 75-117
	#ModeLine "1024x768" 78.75 1024 1044 1140 1328 768 781 784 820 +hsync +vsync
	#ModeLine "800x600" 62.40 800 821 901 1040 600 609 612 644 +hsync +vsync
	#Modeline "640x480" 49.90 640 657 721 832 480 481 484 514 +hsync +vsync
EndSection

Section "Screen"
	Identifier "Default Screen"
	Monitor "Configured Monitor"
	DefaultDepth 16
	SubSection "Display"
		Modes "1024x768" "800x600" "768x576" "640x480"
		Virtual 1024 768
	EndSubSection
EndSection

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection


Section "Module"
	Load 	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load   	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"glx"
	Load	"int10"
	Load	"freetype"
	Load	"type1"
	Load	"vbe"
	Load	"record"
	Load	"v4l"
EndSection

Section "InputDevice"
	Identifier "Generic Keyboard"
	Driver "kbd"
	Option "XkbRules" "xorg"
	Option "XkbModel" "pc105"
	Option "XkbLayout" "us"
	Option "XkbVariant" "intl"
	Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
EndSection

Section "Device"
	Identifier 	"Configured Video Device"
	VendorName 	"ATI Technologies Inc"
	BoardName 	"Rage Mobility M3 AGP 2x"
	Driver 		"ati"
	Option 		"AgpMode" 		"4"
	Option		"AGPFastWrite"		"true"
	Option 		"EnablePageFlip" 	"true"
	Option 		"Accel" 		"true"
	Option 		"AccelMethod"		"EXA"
	Option 		"VideoOverlay" 		"on"
	Option 		"XAANoOffScreenPixmaps"
	Option 		"TripleBuffer"  	"true"
	Option 		"DynamicClocks"  	"on"
	VideoRam 	8192
	Option 		"CCEusecTimeout" 	"100000"
	Option 		"UseFBDev" 		"false"
	Option		"GARTSize"		"64"
	Option 		"AddARGBGLXVisuals"	"true"
	Option 		"AllowGLXWithComposite"	"true"
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

Section "ServerLayout"
	Option "AIGLX" 	"true"
	Identifier "Default Layout"
	Screen "Default Screen"
	InputDevice "Generic Keyboard"
	InputDevice "Configured Mouse"
EndSection
```

if their be [COLOR="Blue"]anyone [/COLOR] who might help, I'll be glad and thankful. I have struggled with this for the last 1 1/2 days, someone please step in and help a fellow human being, Great ubuntuExperience.

---

### Post by linuxopjemac on 2010-05-20
Try adding
```
Option 		"NoInt10"		"true"
```
in the Device section

I would also use the modelines, but that's up to you to decide.

---

### Post by nmvictor on 2010-05-21
> **linuxopjemac said:**
> Try adding
```
Option 		"NoInt10"		"true"
```
in the Device section

I would also use the modelines, but that's up to you to decide.

Thanks, i did an upgrade to lucid lynx, things seem a bit fair with lynx but their are still some issues...
ok, for the above suggestion, i tried but it just got me to screen with green text(the boot texts) which hang for so long, enough to convince me to upgrade to lucid. Their wasn't much difference with lucid, i still needed an xorg.conf to correct my display though i have noticed some minor improvement.
Right now i still cant launch compiz, an attempt at the terminal gives me this: 
```
compiz
compiz (core) - Fatal: Support for non power of two textures missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

```
Videos is playing and am thankful lucid can manage .AVI without much hustle, however, the video lags at some point, something that makes you think of low grephics,it's as if the redrawing of images and motion is a slow. Im not sure if the refresh rate,Horsync and VertSync has has anything to do with it? Check my current xorg.conf below and make suggestions/corrections.... As for the Modeline, i would wish to use that if only to correct my problem, i dont know what would be the appropriate modeline with the settings on my xorg.con below, please help and many thanks [COLOR="green"]linuxopjemac[/COLOR] the much you're doing.

```
# xorg.conf (X.Org X Window System server configuration file)
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier "Configured Monitor"
	HorizSync 58-62
	VertRefresh 75-117
	#ModeLine "1024x768" 78.75 1024 1044 1140 1328 768 781 784 820 +hsync +vsync
	#ModeLine "800x600" 62.40 800 821 901 1040 600 609 612 644 +hsync +vsync
	#Modeline "640x480" 49.90 640 657 721 832 480 481 484 514 +hsync +vsync
EndSection

Section "Screen"
	Identifier "Default Screen"
	Monitor "Configured Monitor"
	DefaultDepth 16
	SubSection "Display"
		Modes "1024x768" "800x600" "768x576" "640x480"
		#Virtual 1024 768
	EndSubSection
EndSection
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load 	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load   	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"glx"
	Load	"int10"
	Load	"freetype"
	Load	"type1"
	Load	"vbe"
	Load	"record"
	Load	"v4l"
EndSection

Section "InputDevice"
	Identifier "Generic Keyboard"
	Driver "kbd"
	Option "XkbRules" "xorg"
	Option "XkbModel" "pc105"
	Option "XkbLayout" "us"
	Option "XkbVariant" "intl"
	Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
EndSection

Section "Device"
	Identifier 	"Configured Video Device"
	VendorName 	"ATI Technologies Inc"
	BoardName 	"Rage Mobility M3 AGP 2x"
	Driver 		"ati"
	Option 		"AgpMode" 		"4"
	Option		"AGPFastWrite"		"true"
	Option 		"EnablePageFlip" 	"true"
	Option 		"Accel" 		"true"
	Option 		"AccelMethod"		"EXA"
	Option 		"VideoOverlay" 		"on"
	Option 		"XAANoOffScreenPixmaps"
	Option		"NoInt10"		"true"
	Option 		"TripleBuffer"  	"true"
	Option 		"DynamicClocks"  	"on"
	VideoRam 	8192
	Option 		"CCEusecTimeout" 	"100000"
	Option 		"UseFBDev" 		"false"
	Option		"GARTSize"		"64"
	#Option 		"AddARGBGLXVisuals"	"true"
	#Option 		"AllowGLXWithComposite"	"true"
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "ServerLayout"
	Option "AIGLX" 	"true"
	Identifier "Default Layout"
	Screen "Default Screen"
	InputDevice "Generic Keyboard"
	InputDevice "Configured Mouse"
EndSection
```

---

### Post by linuxopjemac on 2010-05-21
If the modelines are correct, don't know, (did you make them with cvt?) you can uncomment them to look  like this:

```
Section "Monitor"
	Identifier "Configured Monitor"
	HorizSync 58-62
	VertRefresh 75-117
	ModeLine "1024x768" 78.75 1024 1044 1140 1328 768 781 784 820 +hsync +vsync
	ModeLine "800x600" 62.40 800 821 901 1040 600 609 612 644 +hsync +vsync
	Modeline "640x480" 49.90 640 657 721 832 480 481 484 514 +hsync +vsync
EndSection
```

---

### Post by nmvictor on 2010-05-22
Thanks again, I tried that and only a section of my screen could be visible, the rest was just filled with black.I think its because i picked the start up xorg.conf from [http://takewii.com/index.php?q=aHR0cHM6Ly93aWtpLnVidW50dS5jb20vUG93ZXJQQ0ZBUQ%3D%3D]("http://takewii.com/index.php?q=aHR0cHM6Ly93aWtpLnVidW50dS5jb20vUG93ZXJQQ0ZBUQ%3D%3D") However, the section that was visible was damn fast and cool, seems like the modelines could improve the situation. I don't know whats the appropriate modelines for me? and what is cvt?

---

### Post by linuxopjemac on 2010-05-22
have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1480685&page=3") and give me the same output of
```
cvt 1024 768
cvt 800 600
cvt 640 480
```

---

### Post by nmvictor on 2010-05-23
> **linuxopjemac said:**
> have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1480685&page=3") and give me the same output of
```
cvt 1024 768
cvt 800 600
cvt 640 480
```
Thanks, Here is the output of the above codes in their order
```
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

------------
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync

-------------
# 640x480 59.38 Hz (CVT 0.31M3) hsync: 29.69 kHz; pclk: 23.75 MHz
Modeline "640x480_60.00"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync

I am not sure if I'm supposed to paste the above in xorg.conf, I dont want to make any mistakes so I'll wait for your go ahead.




```

---

### Post by linuxopjemac on 2010-05-24
Just replace the Monitor Section with this:


Section "Monitor"
	Identifier "Configured Monitor"
	HorizSync 58-62
	VertRefresh 75-117
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
Modeline "640x480_60.00"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync
Option "PreferredMode" "1024x768_60"
EndSection

---

