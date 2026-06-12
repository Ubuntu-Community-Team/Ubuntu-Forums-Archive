---
title: "Gutsy Display Issues - NVIDIA TNT2 card"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-10-21
I've just done a clean install of Gutsy (wasn't able to do an upgrade as Update Manager didn't want to work)

Having gone through the aggravation of reinstalling programs, settings, etc (is there a way of backing these up reliably?), I had the issue that display is skewed to the right, so you can't - for example - see the red quit icon in top right hand corner.

Previously in Feisty I'd used ENVY in an attempt to get Beryl to work (it didn't - card just doesn't have the memory), so thought that may resolve this issue too.

Went through install, rebooted, and saw there was an update for me. Pressed on install updates, got message:

```
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first
```

Now, ENVY was the only thing I'd installed since last boot, and bearing in mind the issues this caused me before, I decided (perhaps rashly) to uninstall it.

Rebooted. Can't get in to main set up - get this message:

Out of scan range 63.82kHz / 60Hz

PC just freezes.

Can get in under recovery mode, albeit in glorious 800*600!

How can I get it working again (preferably in 1024*768) for normal sign on?

---

### Post by Qwerty_ on 2007-10-21
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by qprfact on 2007-10-21
I did try that before, but just given it another go....

---

### Post by qprfact on 2007-10-21
Right - how odd is this??!

Boot in Recovery Mode - perfect! Exactly the way I want it to display - right resolution, everything.

But.... boot into normal mode, and I still get the out of scan range message.

The coward's way out at this point would probably be to make booting in recovery mode my default option (and to be honest, I don't turn off and on that much anyway), but if it can work for one, why not the other?!!

---

### Post by qprfact on 2007-10-21
A similar post on this forum suggested running:

```
sudo lshw -C display
```

for which my output was:

```
  *-display
       description: VGA compatible controller
       product: NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 15
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga bus_master cap_list
       configuration: driver=nvidia latency=64 maxlatency=1 mingnt=5 module=nvidia
```

and ```
cat /etc/X11/xorg.conf
```

for which my output was:

```
# xorg.conf (xorg X Window System server configuration file)

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"uk"
	Option		"XkbVariant"	"uk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"F153"
	Option		"DPMS"
	HorizSync	30-61
	VertRefresh	52-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"F153"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

A bit of reading around suggests my HorizSync numbers are out of kilter (maybe that's why the message on the monitor says 63.82kHz / 60Hz?) but I don't know:

1. How to edit them, if that is indeed the case
2. Why display is absolutely fine in recovery mode

Can anyone help please??

Thanks!

---

### Post by JohnSGruber on 2007-10-21
I see you are back to using the free nvidia driver at this point and can't get it to work.

Perhaps it would make sense to try to use Screens and Graphics to select your monitor, or if isn't there, try the detect button.

What kind of monitor is it? Is it a real CRT (they are necessarily very picky about those two frequencies) and you want to make sure that the frequencies used by the computer are compatible.

Once you have everything ok with the free driver nv you can backup your /etc/X11/xorg.conf file and try enabling the proprietary nvidia driver.

Usually to start with there are no frequencies in the file and the nv driver is good about finding the frequencies itself. If the frequencies are in the file and they are wrong it can mess resolutions up.

---

### Post by qprfact on 2007-10-22
Thanks! I tried Screens and Graphics, and the option it presented was a blank screen, and then said:

> Configuration test failed.
Please verify the selected devices and configuration

It currently says Screen is Plug'n'Play, resolution 1024*768, 75Hz, and card is nv - NVidia Riva 128, TNT, GEForce,,,

Changing card to Nvidia seems to have no effect.

I think it is definitely a refresh rate issue, so I amended xorg.conf to remove the 

```
HorizSync	29-61
VertRefresh	49-76
```

bits, and rebooted. Still got the out of scan range message.

As for the monitor, the manual describes it as a "...TFT LCD color monitor". Scan frequencies are:

Horizontal: 30kHz - 60kHz
Vertical: 50Hz - 75Hz

The manual also says this about the message Out of Scan Range:

"The frequency of input signals do not match the F153. Connect different monitor and set the horizontal frequency to some value between 28 to 64 KHz and vertical frequency to same value between 48 to 75 Hz"

But I still can't fathom why it works in recovery mode? Should I manually put the figures in xorg.conf?

---

### Post by JohnSGruber on 2007-10-22
I guess I have a couple of ideas at this point.

One would be to try using Screens and Graphics to set a Generic monitor, LCD 1024x768. I just tried that on my own monitor and it worked, though I usually use Generic, LCD 1280x1024. I assume you have a Vison or GNR and that it's not listed in Screens and Graphics.

Another thought, different modes may use different leads to send the sync, and they do send minus and plus voltage sync voltages. Have you double checked the physical connection between the cable and the monitor and the back of the computer?

Another thought--75 is close to the limit of 76Hz listed for your monitor. Perhaps you could put those lines back in but change the upper limit for the vertical refresh to 70Hz and see what happens. Video drivers like to set high vertical refresh rates to reduce flicker on CRT monitors, but you have a LCD so having a lower vertical refresh doesn't bother the quality of the display.

It could be that recovery mode uses a very basic video mode that won't give you many colors and that may be related to why it works and defaults don't, but that is just a guess.

Finally, to really get into this, it would be best if you could attach the Xorg.0.log files. They are created whenever X starts and show how the nv driver is trying to figure out what modes are good and what modes aren't. Be sure to tell us what you are saw when the particular logs were created.

ps. The GNR specs page for a F153 (is that yours?) says Analogue 0.7 Vp-p separate sync. It could be you are fighting the video driver and card to get that to happen.

Good luck and please write back.

---

### Post by qprfact on 2007-10-22
Hi John, thanks for your reply.

Daft question first - I tried Screens and Graphics - Generic, LCD 1024x768. Should I expect the test screen it produces to actually look like a normal screen, or (as I got it) a screen consisting of very fine black and white wavy lines?

If I get it to detect, it tells me my screen is Plug'n'Play

You are correct, my screen is a GNR F153, and it does indeed say in the manual about Analogue 0.7 Vp-p separate sync.

In terms of colours, the recovery mode seems fine - everything seems to display OK.

This is what Xorg.o.log says (there's an awful lot of it!)

```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux steve-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 22 13:33:42 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "F153"
(**) |   |-->Device "nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
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
(II) Loader magic: 0x81ea440
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
(II) PCI: 00:00:0: chip 8086,1130 card 0000,0000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1131 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 01 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 107b,0058 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 107b,0058 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2443 card 107b,0058 rev 01 class 0c,05,00 hdr 00
(II) PCI: 00:1f:4: chip 8086,2444 card 107b,0058 rev 01 class 0c,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,002d card 1545,0002 rev 15 class 03,00,00 hdr 00
(II) PCI: 02:09:0: chip 1033,0035 card 1033,0035 rev 41 class 0c,03,10 hdr 80
(II) PCI: 02:09:1: chip 1033,0035 card 1033,0035 rev 41 class 0c,03,10 hdr 00
(II) PCI: 02:09:2: chip 1033,00e0 card 1033,00e0 rev 02 class 0c,03,20 hdr 00
(II) PCI: 02:0a:0: chip 1274,1371 card 1274,1371 rev 08 class 04,01,00 hdr 00
(II) PCI: 02:0c:0: chip 109e,036e card 0070,13eb rev 11 class 04,00,00 hdr 80
(II) PCI: 02:0c:1: chip 109e,0878 card 0070,13eb rev 11 class 04,80,00 hdr 80
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
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfc900000 - 0xfe9fffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf0600000 - 0xf46fffff (0x4100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xf4700000 - 0xf47fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] rev 21, Mem @ 0xfd000000/24, 0xf2000000/25, BIOS @ 0xfe9f0000/16
(--) PCI: (2:12:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xf47fe000/12
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
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[1] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[2] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[3] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[4] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[5] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[6] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[7] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[10] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[11] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[12] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[1] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[2] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[3] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[4] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[5] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[6] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[7] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[10] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[11] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[12] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
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
	[4] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[6] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[7] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[8] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[9] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[10] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[11] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[16] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[17] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[18] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
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
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7185
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
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
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 2.1.5
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
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
	GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS,
	GeForce 8600 GT, GeForce 8400 GS, GeForce 8600M GT, GeForce 8700M GT,
	Quadro FX 370, Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M,
	Quadro FX 570, Quadro FX 1700, GeForce 8500 GT, GeForce 8400 GS,
	GeForce 8300 GS, GeForce 8600M GS, GeForce 8400M GT,
	GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
	Quadro NVS 135M, Quadro FX 360M, Quadro NVS 290
(II) Primary Device is: PCI 01:00:0
(--) Chipset RIVA TNT2 Model 64 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[6] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[7] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[8] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[9] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[10] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[11] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[16] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[17] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[18] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[6] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[7] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[8] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[9] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[10] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[11] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[19] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[20] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[21] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "RIVA TNT2 Model 64"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xF2000000
(--) NV(0): MMIO registers at 0xFD000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: GBM  Model: 1530  Serial#: 16843009
(II) NV(0): Year: 2002  Week: 52
(II) NV(0): EDID Version: 1.2
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NV(0): Sync:  Separate  Composite  SyncOnGreen
(II) NV(0): Max H-Image Size [cm]: horiz.: 31  vert.: 23
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.633 redY: 0.336   greenX: 0.294 greenY: 0.614
(II) NV(0): blueX: 0.146 blueY: 0.097   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 720  vsize 540  refresh: 60  vid: 16443
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 65.0 MHz   Image Size:  311 x 234 mm
(II) NV(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) NV(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) NV(0): Stereo: left channel on sync
side-by-side interleaved(II) NV(0): Ranges: V min: 49  V max: 76 Hz, H min: 29  H max: 61 kHz, PixClock max 100 MHz
(II) NV(0): Monitor name: F153
(II) NV(0): Serial No: 08354
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff001c4d301501010101
(II) NV(0): 	340c01020e1f1778ea05b5a2564b9d25
(II) NV(0): 	185054a56e003b400101010101010101
(II) NV(0): 	01010101010164190040410026301888
(II) NV(0): 	360037ea1000007f000000fd00314c1d
(II) NV(0): 	3d0a000a202020202020000000fc0046
(II) NV(0): 	3135330a2020202020202020000000ff
(II) NV(0): 	0030383335340a202020202020200000
(II) NV(0): Using CRT on CRTC 0
(II) NV(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
(II) NV(0): Using EDID range info for horizontal sync
(II) NV(0): Using EDID range info for vertical refresh
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) NV(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) NV(0): Modeline "720x540"   30.50  720 752 816 912  540 543 547 562 -hsync +vsync
(--) NV(0): VideoRAM: 32768 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): F153: Using hsync range of 29.00-61.00 kHz
(II) NV(0): F153: Using vrefresh range of 49.00-76.00 Hz
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (vrefresh out of range)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (vrefresh out of range)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (vrefresh out of range)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (vrefresh out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (mode clock too high)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (mode clock too high)
(II) NV(0): Not using default mode "1600x1024" (hsync out of range)
(II) NV(0): Not using default mode "800x512" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NV(0): Not using default mode "1152x768" (width too large for virtual size)
(--) NV(0): Virtual size is 1024x768 (pitch 1024)
(**) NV(0): *Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0):  Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) NV(0):  Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0):  Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) NV(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) NV(0):  Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) NV(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) NV(0):  Driver mode "720x540": 30.5 MHz, 33.4 kHz, 59.5 Hz
(II) NV(0): Modeline "720x540"   30.50  720 752 816 912  540 543 547 562 -hsync +vsync
(**) NV(0):  Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) NV(0): Modeline "720x450"   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync
(**) NV(0):  Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 -hsync -vsync
(**) NV(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) NV(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(**) NV(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) NV(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) NV(0):  Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) NV(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "512x384"   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) NV(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) NV(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) NV(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(**) NV(0): Display dimensions: (310, 230) mm
(**) NV(0): DPI set to (83, 84)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[7] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[8] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[9] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[12] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[13] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[21] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[22] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[23] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xf2000000,0x2000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
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
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "uk"
(**) Generic Keyboard: XkbLayout: "uk"
(**) Option "XkbVariant" "uk"
(**) Generic Keyboard: XkbVariant: "uk"
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
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
```

I'll try your suggestion with manually inputting sync rates and post back what happens....

Thanks!!!

---

### Post by qprfact on 2007-10-22
I tried with the following settings:

```
Section "Monitor"
	Identifier	"F153"
	Option		"DPMS"
	HorizSync	29-61
	VertRefresh	49-70
EndSection
```

And it didn't work. One thing I've just noticed in xorg.conf tho' - there is a "Screen" entry and a "Monitor" entry, with the former referring to my video card rather than the monitor itself. Is that right? My entire xorg.conf is:

```
# xorg.conf (xorg X Window System server configuration file)
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
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"uk"
	Option		"XkbVariant"	"uk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"F153"
	Option		"DPMS"
 	HorizSync	29-61
 	VertRefresh	49-70
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"F153"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

---

### Post by JohnSGruber on 2007-10-22
When you make the change in Screens and Graphics the result should look fine.

I think your xorg.conf file looks ok. The screen section is pointing to both the nvidia device section and to your monitor and I think that is fine.

By saying that changing the frequencies in the file didn't work I assume you mean you get an error on the monitor, not that it doesn't display right or with the wrong resolution. Is that correct? Could you describe what steps you are taking and when you see what you see so I can be sure I'm understanding?

It would be nice to see the Xorg.0.log file from when you try this. If you have to get to safe mode to get it you may have to go to the Xorg.0.log.old file which is the file one generation older. You can tell which one to attach by looking at the files creation time. Applications->Accessories->Terminal->

```
ls -lt  /var/log/Xorg*
```

You probably know that but just in case.

I'd be curious to see how many display modes were eliminated by entering those frequencies by hand. There were a few modes that were between the frequencies the monitor returned to the driver and those published by the vendor, which were always 2 units narrower if you look at the big log you attached.

When you boot normally does the monitor give the message right away or when it is time to sign on? If it is when it is time to sign on does it work to enter CTL-ALT-F1? As you probably know you press CTL-ALT-F7 to go back. (Beginners may be watching this thread).

Finally, when you are looking at that message the monitor is giving you have you tried to use the code sequence CTL-ALT- + and CTL-ALT- -  (where the + and - are the ones on the numeric keyboard not on the main part of the keyboard)? That will bring you through all of the modes one by one. Looks like there were 37 of them before you edited the file, which should have brought down the number of mode choices by a couple.

The modes the driver thinks your monitor will support are indicated in the log by the modelines. They are the ones that look like:

```

*Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync

...

```
You can see that the very first mode line has a vertical refresh rate of 75.1 Hz which is less than the 76Hz limit returned by the monitor electronically but .1Hz above the specification published by the manufacturer.

---

### Post by qprfact on 2007-10-22
Hi John - some answers for you!

The "Out of scan range" message appears almost immediately, certainly long before sign on time, and I think follows the "Starting up" message that appears on top of screen,

I didn't know about Alt-F1, so haven't tried that yet.

Xorg.0.log.old is as follows:

```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux steve-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 22 13:33:42 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "F153"
(**) |   |-->Device "nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
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
(II) Loader magic: 0x81ea440
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
(II) PCI: 00:00:0: chip 8086,1130 card 0000,0000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1131 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 01 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 107b,0058 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 107b,0058 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2443 card 107b,0058 rev 01 class 0c,05,00 hdr 00
(II) PCI: 00:1f:4: chip 8086,2444 card 107b,0058 rev 01 class 0c,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,002d card 1545,0002 rev 15 class 03,00,00 hdr 00
(II) PCI: 02:09:0: chip 1033,0035 card 1033,0035 rev 41 class 0c,03,10 hdr 80
(II) PCI: 02:09:1: chip 1033,0035 card 1033,0035 rev 41 class 0c,03,10 hdr 00
(II) PCI: 02:09:2: chip 1033,00e0 card 1033,00e0 rev 02 class 0c,03,20 hdr 00
(II) PCI: 02:0a:0: chip 1274,1371 card 1274,1371 rev 08 class 04,01,00 hdr 00
(II) PCI: 02:0c:0: chip 109e,036e card 0070,13eb rev 11 class 04,00,00 hdr 80
(II) PCI: 02:0c:1: chip 109e,0878 card 0070,13eb rev 11 class 04,80,00 hdr 80
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
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfc900000 - 0xfe9fffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf0600000 - 0xf46fffff (0x4100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xf4700000 - 0xf47fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] rev 21, Mem @ 0xfd000000/24, 0xf2000000/25, BIOS @ 0xfe9f0000/16
(--) PCI: (2:12:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xf47fe000/12
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
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[1] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[2] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[3] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[4] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[5] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[6] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[7] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[10] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[11] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[12] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[1] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[2] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[3] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[4] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[5] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[6] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[7] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[10] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[11] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[12] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
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
	[4] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[6] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[7] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[8] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[9] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[10] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[11] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[16] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[17] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[18] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
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
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7185
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
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
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 2.1.5
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
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
	GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS,
	GeForce 8600 GT, GeForce 8400 GS, GeForce 8600M GT, GeForce 8700M GT,
	Quadro FX 370, Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M,
	Quadro FX 570, Quadro FX 1700, GeForce 8500 GT, GeForce 8400 GS,
	GeForce 8300 GS, GeForce 8600M GS, GeForce 8400M GT,
	GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
	Quadro NVS 135M, Quadro FX 360M, Quadro NVS 290
(II) Primary Device is: PCI 01:00:0
(--) Chipset RIVA TNT2 Model 64 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[6] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[7] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[8] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[9] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[10] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[11] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[16] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[17] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[18] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[6] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[7] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[8] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[9] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[10] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[11] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[19] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[20] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[21] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "RIVA TNT2 Model 64"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xF2000000
(--) NV(0): MMIO registers at 0xFD000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: GBM  Model: 1530  Serial#: 16843009
(II) NV(0): Year: 2002  Week: 52
(II) NV(0): EDID Version: 1.2
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NV(0): Sync:  Separate  Composite  SyncOnGreen
(II) NV(0): Max H-Image Size [cm]: horiz.: 31  vert.: 23
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.633 redY: 0.336   greenX: 0.294 greenY: 0.614
(II) NV(0): blueX: 0.146 blueY: 0.097   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 720  vsize 540  refresh: 60  vid: 16443
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 65.0 MHz   Image Size:  311 x 234 mm
(II) NV(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) NV(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) NV(0): Stereo: left channel on sync
side-by-side interleaved(II) NV(0): Ranges: V min: 49  V max: 76 Hz, H min: 29  H max: 61 kHz, PixClock max 100 MHz
(II) NV(0): Monitor name: F153
(II) NV(0): Serial No: 08354
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff001c4d301501010101
(II) NV(0): 	340c01020e1f1778ea05b5a2564b9d25
(II) NV(0): 	185054a56e003b400101010101010101
(II) NV(0): 	01010101010164190040410026301888
(II) NV(0): 	360037ea1000007f000000fd00314c1d
(II) NV(0): 	3d0a000a202020202020000000fc0046
(II) NV(0): 	3135330a2020202020202020000000ff
(II) NV(0): 	0030383335340a202020202020200000
(II) NV(0): Using CRT on CRTC 0
(II) NV(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
(II) NV(0): Using EDID range info for horizontal sync
(II) NV(0): Using EDID range info for vertical refresh
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) NV(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) NV(0): Modeline "720x540"   30.50  720 752 816 912  540 543 547 562 -hsync +vsync
(--) NV(0): VideoRAM: 32768 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): F153: Using hsync range of 29.00-61.00 kHz
(II) NV(0): F153: Using vrefresh range of 49.00-76.00 Hz
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (vrefresh out of range)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (vrefresh out of range)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (vrefresh out of range)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (vrefresh out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (mode clock too high)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (mode clock too high)
(II) NV(0): Not using default mode "1600x1024" (hsync out of range)
(II) NV(0): Not using default mode "800x512" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NV(0): Not using default mode "1152x768" (width too large for virtual size)
(--) NV(0): Virtual size is 1024x768 (pitch 1024)
(**) NV(0): *Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0):  Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) NV(0):  Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0):  Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) NV(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) NV(0):  Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) NV(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) NV(0):  Driver mode "720x540": 30.5 MHz, 33.4 kHz, 59.5 Hz
(II) NV(0): Modeline "720x540"   30.50  720 752 816 912  540 543 547 562 -hsync +vsync
(**) NV(0):  Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) NV(0): Modeline "720x450"   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync
(**) NV(0):  Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 -hsync -vsync
(**) NV(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) NV(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(**) NV(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) NV(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) NV(0):  Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) NV(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "512x384"   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) NV(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) NV(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) NV(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(**) NV(0): Display dimensions: (310, 230) mm
(**) NV(0): DPI set to (83, 84)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[7] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[8] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[9] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[12] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[13] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[21] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[22] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[23] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xf2000000,0x2000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
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
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "uk"
(**) Generic Keyboard: XkbLayout: "uk"
(**) Option "XkbVariant" "uk"
(**) Generic Keyboard: XkbVariant: "uk"
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
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
```

Yes, changing frequencies meant I got no display, just the fine wavy lines.

I'll try the CTRL-ALT-+ in the morning - thanks for the tip!

---

### Post by JohnSGruber on 2007-10-22
Whoops, that is ALT-CTL-F1, holding both ALT and CTL while pressing F1.

The file you just posted is the same one you posted earlier, I'm afraid. You can tell which file is which by looking at the log creation line, the 13th line in the log file. They were from 13:33 this afternoon. When X starts it throws away Xorg.0.log.old, moves Xorg.0.log to Xorg.0.log.old, and then creates a new Xorg.0.log. Looks like you rebooted or restarted X between the postings.

Good luck in the morning.

---

### Post by qprfact on 2007-10-23
Hi John!

CTRL-ALT & F1 worked, it continued booting and brought me into a session. Does that fix it do you think, or would I need to do that with each boot?

As for the log files, it doesn't surprise me they are the same, as I tried so many times! However, this is the one from just booting, which I suppose is the one that will (if any will!) show the errors....

```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux steve-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 23 09:19:25 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "F153"
(**) |   |-->Device "nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
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
(II) Loader magic: 0x81ea440
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
(II) PCI: 00:00:0: chip 8086,1130 card 0000,0000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1131 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 01 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 107b,0058 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 107b,0058 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2443 card 107b,0058 rev 01 class 0c,05,00 hdr 00
(II) PCI: 00:1f:4: chip 8086,2444 card 107b,0058 rev 01 class 0c,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,002d card 1545,0002 rev 15 class 03,00,00 hdr 00
(II) PCI: 02:09:0: chip 1033,0035 card 1033,0035 rev 41 class 0c,03,10 hdr 80
(II) PCI: 02:09:1: chip 1033,0035 card 1033,0035 rev 41 class 0c,03,10 hdr 00
(II) PCI: 02:09:2: chip 1033,00e0 card 1033,00e0 rev 02 class 0c,03,20 hdr 00
(II) PCI: 02:0a:0: chip 1274,1371 card 1274,1371 rev 08 class 04,01,00 hdr 00
(II) PCI: 02:0c:0: chip 109e,036e card 0070,13eb rev 11 class 04,00,00 hdr 80
(II) PCI: 02:0c:1: chip 109e,0878 card 0070,13eb rev 11 class 04,80,00 hdr 80
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
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfc900000 - 0xfe9fffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf0600000 - 0xf46fffff (0x4100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xf4700000 - 0xf47fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] rev 21, Mem @ 0xfd000000/24, 0xf2000000/25, BIOS @ 0xfe9f0000/16
(--) PCI: (2:12:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xf47fe000/12
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
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[1] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[2] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[3] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[4] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[5] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[6] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[7] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[10] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[11] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[12] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[1] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[2] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[3] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[4] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[5] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[6] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[7] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[10] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[11] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[12] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
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
	[4] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[6] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[7] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[8] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[9] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[10] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[11] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[16] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[17] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[18] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
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
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7185
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
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
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 2.1.5
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
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
	GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS,
	GeForce 8600 GT, GeForce 8400 GS, GeForce 8600M GT, GeForce 8700M GT,
	Quadro FX 370, Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M,
	Quadro FX 570, Quadro FX 1700, GeForce 8500 GT, GeForce 8400 GS,
	GeForce 8300 GS, GeForce 8600M GS, GeForce 8400M GT,
	GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
	Quadro NVS 135M, Quadro FX 360M, Quadro NVS 290
(II) Primary Device is: PCI 01:00:0
(--) Chipset RIVA TNT2 Model 64 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[6] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[7] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[8] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[9] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[10] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[11] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[16] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[17] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[18] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[6] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[7] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[8] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[9] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[10] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[11] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[19] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[20] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[21] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "RIVA TNT2 Model 64"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xF2000000
(--) NV(0): MMIO registers at 0xFD000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: GBM  Model: 1530  Serial#: 16843009
(II) NV(0): Year: 2002  Week: 52
(II) NV(0): EDID Version: 1.2
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NV(0): Sync:  Separate  Composite  SyncOnGreen
(II) NV(0): Max H-Image Size [cm]: horiz.: 31  vert.: 23
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.633 redY: 0.336   greenX: 0.294 greenY: 0.614
(II) NV(0): blueX: 0.146 blueY: 0.097   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 720  vsize 540  refresh: 60  vid: 16443
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 65.0 MHz   Image Size:  311 x 234 mm
(II) NV(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) NV(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) NV(0): Stereo: left channel on sync
side-by-side interleaved(II) NV(0): Ranges: V min: 49  V max: 76 Hz, H min: 29  H max: 61 kHz, PixClock max 100 MHz
(II) NV(0): Monitor name: F153
(II) NV(0): Serial No: 08354
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff001c4d301501010101
(II) NV(0): 	340c01020e1f1778ea05b5a2564b9d25
(II) NV(0): 	185054a56e003b400101010101010101
(II) NV(0): 	01010101010164190040410026301888
(II) NV(0): 	360037ea1000007f000000fd00314c1d
(II) NV(0): 	3d0a000a202020202020000000fc0046
(II) NV(0): 	3135330a2020202020202020000000ff
(II) NV(0): 	0030383335340a202020202020200000
(II) NV(0): Using CRT on CRTC 0
(II) NV(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
(II) NV(0): Using EDID range info for horizontal sync
(II) NV(0): Using EDID range info for vertical refresh
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) NV(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) NV(0): Modeline "720x540"   30.50  720 752 816 912  540 543 547 562 -hsync +vsync
(--) NV(0): VideoRAM: 32768 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): F153: Using hsync range of 29.00-61.00 kHz
(II) NV(0): F153: Using vrefresh range of 49.00-76.00 Hz
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (vrefresh out of range)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (vrefresh out of range)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (vrefresh out of range)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (vrefresh out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (mode clock too high)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (mode clock too high)
(II) NV(0): Not using default mode "1600x1024" (hsync out of range)
(II) NV(0): Not using default mode "800x512" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NV(0): Not using default mode "1152x768" (width too large for virtual size)
(--) NV(0): Virtual size is 1024x768 (pitch 1024)
(**) NV(0): *Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0):  Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) NV(0):  Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0):  Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) NV(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) NV(0):  Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) NV(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) NV(0):  Driver mode "720x540": 30.5 MHz, 33.4 kHz, 59.5 Hz
(II) NV(0): Modeline "720x540"   30.50  720 752 816 912  540 543 547 562 -hsync +vsync
(**) NV(0):  Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) NV(0): Modeline "720x450"   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync
(**) NV(0):  Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 -hsync -vsync
(**) NV(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) NV(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(**) NV(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) NV(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) NV(0):  Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) NV(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "512x384"   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) NV(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) NV(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) NV(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(**) NV(0): Display dimensions: (310, 230) mm
(**) NV(0): DPI set to (83, 84)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xf47ff000 - 0xf47fffff (0x1000) MX[B]
	[7] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[8] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[9] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xf47fe000 - 0xf47fefff (0x1000) MX[B](B)
	[12] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[13] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[21] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[22] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[23] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xf2000000,0x2000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
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
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "uk"
(**) Generic Keyboard: XkbLayout: "uk"
(**) Option "XkbVariant" "uk"
(**) Generic Keyboard: XkbVariant: "uk"
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
SetClientVersion: 0 9
Got unexpected buttonTimer in state 0
```

---

### Post by JohnSGruber on 2007-10-23
So if you press CTL-ALT-F1 it let's you log on and works ok? If you don't and get the error message and wait 5 minutes will you eventually get the logon screen?

I think to avoid the monitor's message you will have to fix the Ubuntu splash screen.What does your /etc/usplash.conf file have in it? If it is bigger than your screen can handle you should be able to edit it and maybe get the splash screen to display properly. Mine has 1280x1024 which is the biggest my LCD monitor can handle but would be too big for yours. However I don't know how the file gets created.

Going forward, I believe you have a legacy nvidia video card and I assume you will therefore be using Xgl. Once you are ready to try that make sure that the following option remains in your xorg.conf file or you will probably have trouble logging on:

```
Option "AllowGLXWithComposite" "True"
```

Enabling the proprietary driver (nvidia) will automatically add that, but it can be eliminated by the Screens and Graphic control.

I know you aren't afraid to edit your file so I won't bother with the gory details on how to get it in there without doing the editing. There is a fail-safe gnome session you can reach through the option selection at the bottom left of the sign-on screen should you need it.

Just so you know for the future, The X server that was creating the log files doesn't start until the screen flashes and you are presented with the logon screen. Everything before that is just Linux using whatever drivers it has access to.

Good luck, and please post with your experiences.

---

### Post by qprfact on 2007-10-23
I was too impatient to wait 5 minutes! But the CTRL ALT F1 did bring up all the other system messages and then the log in screen. Interestingly, a combination of CTRL ALT + and CTRL ALT - hit in a seemingly random fashion also brought up a login screen!

My /etc/usplash.conf says exactly the same as yours. I think I'll leave alone!

I tried to get all the whizzy displays in Feisty, but my video card just couldn't cope with it, so I won't be trying again in Gutsy!

Thanks again!

---

### Post by qprfact on 2007-10-27
Leaving the screen alone for a few minutes does allow it to continue to the sign on screen.

---

### Post by qprfact on 2007-11-03
I tried this and now all seems OK:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)

---

