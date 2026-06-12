---
title: "[SOLVED] xserver wont start after 7.04upgrade PPCG4dual"
date: 2007-08-21
forum: Apple PPC Users
---

### Post by frog_pilot on 2007-08-21
hi there

i have installed ubuntu edgy (6.10) on my powermac G4 dual. it has a radeon9000 with 64 MB and a compaq P110 monitor. everything worked fine on 1600x1200@85Hz. In xorg.conf i selected "radeon" in the driver-section.

the only problem was with the splash-screen. it was orange with green dots. but i didn't worried about, because the gui worked very well.

after the upgrade to feisty (7.04) the splash-screen turned black/white and after trying to start the xserver, the server terminates with a "Caught signal 7" error (i think it displays an I/O error, but not shure - I'm not on this machine now).

this problem remains the same when i install 7.04 on an emty disc. the upgrade was on a fresh installed edgy. only changed the kernel-metapakage.

But I can't find any changes in the xorg.conf after the upgrade. every entry is the same like in the old working 6.10 system (maybe the modules-section was altered...:confused: ).

Did anybody experienced similar problems? and has a solution? :-k

---

### Post by renzokuken on 2007-08-21
try running

```
sudo dpkg-reconfigure xserver-xorg
```

and select you xorg settings that way,

---

### Post by frog_pilot on 2007-08-21
as i said: i mentioned no change in the xorg.conf file after the upgrade and i did several attempts with ```
dpkg-reconfigure xserver-xorg
``` to solve this problem

because of the black/white splashscreen (this status-bar thing), i thought the xserver-problem is a graphic-issue. that's why itried different drivers (ati, radeon), with and without videoram entry, with differnt screen-settings

but nothing worked....

---

### Post by frog_pilot on 2007-08-21
i did another attempt to fix my problem ... nothing is working

i took a backup of my perfectly working xorg.conf from edgy. in feisty it won't work.

lspci | grep VGA says:
```
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
```

in Xorg.0.log i find:
```
(II) Primary Device is: PCI 00:10:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]".
(--) Chipset ATI Radeon 9000/PRO If (AGP/PCI) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf1000000 - 0xf101ffff (0x20000) MX[B](B)
	[5] -1	0	0x90000000 - 0x9000ffff (0x10000) MX[B](B)
	[6] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[9] -1	0	0xf0000400 - 0xf00004ff (0x100) IX[B](B)
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 4.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
[COLOR="DarkOrange"](WW) ****INVALID IO ALLOCATION**** b: 0xf0000400 e: 0xf00004ff correcting[/COLOR]
(EE) end of block range 0xefffffff < begin 0xf0000000
(II) window:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) resSize:
(II) window fixed:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf1000000 - 0xf101ffff (0x20000) MX[B](B)
	[5] -1	0	0x90000000 - 0x9000ffff (0x10000) MX[B](B)
	[6] -1	0	0x98000000 - 0x9fffffff (0x8000000) MX[B](B)
	[7] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[8] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[9] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[10] -1	0	0x00000400 - 0x000004ff (0x100) IX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] 0	0	0xf00003b0 - 0xf00003bb (0xc) IS[B]
	[14] 0	0	0xf00003c0 - 0xf00003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) RADEON(0): RADEONPreInit
(II) RADEON(0): MMIO registers at 0x90000000: size 64KB
(II) RADEON(0): PCI bus 0 card 16 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(**) RADEON(0): Option "UseFBDev" "true"
(II) RADEON(0): VGAAccess option set to FALSE, VGA module load skipped
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) RADEON(0): Assuming overlay scaler buffer width is 1536
(++) RADEON(0): "-dpi 100" given in command line, assuming "ConstantDPI" set
(++) RADEON(0): X server will keep DPI constant for all screen sizes
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.0.2
	ABI class: X.Org Video Driver, version 1.1
(**) RADEON(0): Using framebuffer device
(--) RADEON(0): Chipset: "ATI Radeon 9000/PRO If (AGP/PCI)" (ChipID = 0x4966)
(--) RADEON(0): Linear framebuffer at 0x98000000
(--) RADEON(0): BIOS at 0xf1000000
(II) RADEON(0): AGP card detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:10.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:00:10.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.25.0
(II) RADEON(0): AGP Fast Write disabled by default
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules//libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) RADEON(0): Page flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=65536K, accessible=65536K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 65536 kByte (128 bit DDR SDRAM)
(WW) RADEON(0): Color tiling not supported with UseFBDev option
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules//libi2c.so
(II) RADEON(0): I2C bus "DDC" initialized.
(WW) RADEON(0): Not an x86 BIOS ROM image, BIOS data will not be used
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): VBE DDC probing on port 1 ::: 
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(0): initializing int10
(II) RADEON(0): No legacy BIOS found -- trying PCI
(II) Attempted to read BIOS 128KB from /sys/bus/pci/devices/0000:00:10.0/rom: got 95KB

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x94) [0x10090c04]
1: [0x100344]
2: /usr/lib/xorg/modules//libint10.so(LockLegacyVGA+0x50) [0xf8caa50]
3: /usr/lib/xorg/modules//libint10.so(xf86ExtendedInitInt10+0x300) [0xf8cd690]
4: /usr/lib/xorg/modules//libvbe.so(VBEExtendedInit+0x2e0) [0xf87ca70]
5: /usr/lib/xorg/modules//libvbe.so(VBEInit+0x28) [0xf87cc28]
6: /usr/lib/xorg/modules/drivers//radeon_drv.so(RADEONProbeDDC+0x48) [0xf76f558]
7: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xf7799c8]
8: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xf77a584]
9: /usr/lib/xorg/modules/drivers//radeon_drv.so(RADEONPreInit+0xf20) [0xf77b530]
10: /usr/bin/X11/X(InitOutput+0xb08) [0x1006b4e8]
11: /usr/bin/X11/X(main+0x294) [0x1002b964]
12: /lib/libc.so.6 [0xfc5ad40]
13: /lib/libc.so.6 [0xfc5af98]

Fatal server error:
Caught signal 7.  Server aborting

```
the right device is detected, but there seems to be a problem with the videoram...
but on edgy it works. any ideas?

---

### Post by amadain on 2007-08-21
Try this..

In you xorg.conf file, find the device section for your card and

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AP [Radeon 9600]"
#	Driver		"fbdev"
	Driver		"ati"
	BusID		"PCI:240:16:0"
...
...
EndSection

and add the line

	Option          "NoInt10"       	"yes"


The problem is due to a debian/ubultu update in the ati/radeon driver that tries to read x86 BIOS even on a PPC machine. The NoInt10 option tells the driver not to do this.

I hope it works.

My xorg.conf is

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Disable	"int10"
#	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"dbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
#	Option		"XkbLayout"	"us"
#	Option		"XkbOptions"	"lv3:ralt_switch"
	Option		"XkbVariant"	"intl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AP [Radeon 9600]"
#	Driver		"fbdev"
	Driver		"ati"
	BusID		"PCI:240:16:0"
	Option          "NoInt10"       	"yes"
#	Option		"UseFBDev"		"true"
	Option		"AGPMode"		"4"
	Option		"AGPFastWrite"		"1"
	#Option 	"UseInternalAGPGART" 	"no"
	Option 		"UseInternalAGPGART" 	"yes"
	Option		"AccelMethod"		"XAA"
	Option		"EnablePageFlip"	"1"
	Option		"AccelDFS"		"0"
	Option          "RenderAccel" 		"on"
#	Option		"GARTSize"		"64"
#	Option		"GARTSize"		"32"
	Option		"ColorTiling"		"1"
	Option		"XAANoOffscreenPixmaps"	"true"
	Option          "MergedXinerama" 	"true"
	Option          "DRI" 			"true"
EndSection

Section "Monitor"
	Identifier	"Apple Cinema"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Monitor		"Apple Cinema"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		#Modes		"1680x1050" "1024x768" "800x600" "640x480"
		Modes		"1680x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option          "AIGLX"  	"true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

---

### Post by frog_pilot on 2007-08-21
> **amadain said:**
> Try this..
and add the line

	Option          "NoInt10"       	"yes"


The problem is due to a debian/ubultu update in the ati/radeon driver that tries to read x86 BIOS even on a PPC machine. The NoInt10 option tells the driver not to do this.

I hope it works.

hi hi amadain
your solution works...
I am actually writing from a 7.04-live-system with an edited xorg.conf. I think I will start a new upgrade now after finishing a fresh install of edgy :lolflag:

hopefully it will also work for an installed system. 

**another question:**
are these many options in your xorg.conf's graphics-section for a composite-manager?

Which combination do you use? Only the Free ATI-Driver with AIGLX and running beryl?

why did you disable ```
# Option "UseFBDev" "true"
```??? What is it for?

Did you tweak these many options manually into your xorg.conf? or was it an install routine? Is there a manual with explanations anywhere available?

best regards

---

### Post by amadain on 2007-08-21
Hi there frog_pilot,

I am glad that the noint10 option works for you . It actually took me a long time to find.

I use compiz - I used to use Beryl and then I switched - no real reason really - maybe because compiz is now a part of ubuntu-desktop.

I included my xorg.conf file to spark this type of conversation, as I never really obtained good glxgears FPS before. With this configuration, I get 1800FPS or more. I can't say why one line may have a specific value - I have tweaked this configuration so much and am now very impressed with how fast Beryl and Compiz both manage the desktop - it is so fast .

There are many tutorials on how to configure ATI for Beryl and/or Compiz - these were the basis for 80% of the configuration. The remaining 20% came from forums such as this where  someone with a similar configuration specified - a search on Google for " xorg.conf radeon options howto " is already a good start. [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) also helps.

Best of luck.

---

### Post by frog_pilot on 2007-08-22
Thank you amadain for these references.

After another install of feisty the ppc-option for xorg.conf works very well.

thanks for the offer of google-search-words. :oops:  ;)

after beryl didn't work without stuttering on i386 with 1,6 GHZ+128 MB nvidia im looking forward to see compiz-fusion running on a mac :D

Again: thanks a lot for your help

---

