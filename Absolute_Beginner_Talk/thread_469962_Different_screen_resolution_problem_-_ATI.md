---
title: "Different screen resolution problem - ATI"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by tajmox on 2007-06-10
The display modes on the gnome screen resolution chooser **do not** match what is in my xorg.conf.

Fglrx gives me my nice 1680x1050, but some other resolutions which are useless to me:
Gnome screen resolution gui lists these modes, but they are not in my xorg.conf and I don't need them:
1280x1024, 1280x720, 1152x864, 1024x768, 800x600, 640x480      
These aren't even listed in my xorg.conf!  I do not need them and I must have wide screen modes.

[LIST]
[*]I have done dpkg-reconfigure xserver-xorg, and also have done aticonfig --resolution [modes]
[*]I have tried the 'ati' driver
[*]I have removed those Viewport lines in the mode subsections
[*]I have tried many variations of the xorg.conf file
[*]The screen resolutions available in the gnome chooser remain the same
[*]My display is a 16:10 wide screen LCD.
[/LIST]

The modes that I absolutely need are listed here in my /etc/X11/xorg.conf
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 84.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050" "1280x800" "1280x768" "1280x720" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050" "1280x800" "1280x768" "1280x720" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050" "1280x800" "1280x768" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050" "1280x800" "1280x768" "1280x720" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050" "1280x800" "1280x768" "1280x720" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050" "1280x800" "1280x768" "1280x720" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1680x1050" "1280x800" "1280x768" "1280x720" "1024x768" "800x600"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

```

fglrxinfo output:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version string: 2.0.6334 (8.34.8)
```

**Please help.  Thanks!**

---

### Post by muximus on 2007-06-12
you can manually add those resolutions to your xorg.conf and they would work. but i dont think they would be very useful to you considering you have a widescreen display

---

### Post by Najand on 2007-06-12
'ati' driver does not support different resolutions.
Try changing the resolution using:
```

sudo dpkg-reconfigure xserver-xorg

```
Go and find the resolution section, uncheck the ones you don't need... (Remember: It always selects the highest resolution, so it is not a good idea to check all of them)
After configuring the X, restart it using Ctrl+Alt+BackSpace.

---

### Post by kittyhawk63 on 2007-06-12
> **Najand said:**
> 'ati' driver does not support different resolutions.
Try changing the resolution using:
```

sudo dpkg-reconfigure xserver-xrog

```Go and find the resolution section, uncheck the ones you don't need... (Remember: It always selects the highest resolution, so it is not a good idea to check all of them)
After configuring the X, restart it using Ctrl+Alt+BackSpace.

If he didn't catch it, it is:
 sudo dpkg-reconfigure xserver-**xorg  **(not xrog) -just a typo

---

### Post by Najand on 2007-06-12
> **kittyhawk63 said:**
> If he didn't catch it, it is:
 sudo dpkg-reconfigure xserver-**xorg  **(not xrog) -just a typo

Sorry, I edited it.

---

### Post by tajmox on 2007-06-12
> **muximus said:**
> you can manually add those resolutions to your xorg.conf and they would work. but i dont think they would be very useful to you considering you have a widescreen display

Notice that the modes that are in my xorg.conf are the modes that I _need_.
The modes I mentioned on the top are the modes that are available, which are useless to me.

---

### Post by tajmox on 2007-06-12
> **Najand said:**
> 'ati' driver does not support different resolutions.
Try changing the resolution using:
```

sudo dpkg-reconfigure xserver-xorg

```
Go and find the resolution section, uncheck the ones you don't need... (Remember: It always selects the highest resolution, so it is not a good idea to check all of them)
After configuring the X, restart it using Ctrl+Alt+BackSpace.

Notice the bullets section at the top of my post.  I have already re-configured the xorg server, and chose the modes that I need.   They do not appear in the screen resolution chooser after reboot.  It is always the same modes.   Also, I am using the fglrx driver, not the ati driver.  (See xorg.conf file).


**Updated detailed explanation:**

My xorg.conf file confains the screen modes that I need.
These modes are not available to me when I try to change the resolution.    

Example:    
The resolution 1024x768 is listed as a choice in the Gnome screen resolution chooser, but is not anywhere in my xorg.conf file.   
Where is it getting this mode from?  How do I stop it from overriding my xorg.conf?

---

### Post by phollos on 2007-06-12
Hmm okay I had the exact same problem as you setting up my 1680x1050 resolution monitor. I remember being REALLY frustrated because my xorg file didn't match the available resolutions just like you're experiencing.

I can't for the life of me figure out *exactly* what I did though to fix it though! =(

There were only 2 things that I messed with to fix it if I remember correctly. I installed the fglrx driver for my ati card, and I updated my monitor from "generic monitor" to "Dell 2005FPW". I'm pretty sure that was what caused it to work all of a sudden because it automatically entered the resolutions I needed into my xorg.conf file. So I'd try updating your monitor information.

Here's a clip from my xorg.conf file if it will help anyone else pinpoint the problem a little better:
```

...
Section "Device"
  identifier "ATI Technologies Inc R420 JK [Radeon X800]"
  boardname "ATI Radeon (fglrx)"
  busid "PCI:1:0:0"
  driver "ati"
  screen 0
  vendorname "ATI"
  option "MergedFB" "off"
EndSection

Section "Monitor"
  identifier "DELL 2005FPW"
  vendorname "Dell"
  modelname "Dell 1905FP (Digital)"
  HorizSync 30.0-81.0
  VertRefresh 56.0-76.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "ATI Technologies Inc R420 JK [Radeon X800]"
  Monitor "DELL 2005FPW"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1280x800@60" "1440x900@75" "1280x768@75" "1440x900@60" "1280x800@75" "1600x1024@60" "1280x720@60" "1680x1050@60" "1280x768@60" "1920x1200@60" "800x600@60" "800x600@75" "800x600@72" "800x600@56"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
  Mode 0666
EndSection
Section "device" # 
  identifier "device1"
  boardname "ATI Radeon (fglrx)"
  busid "PCI:1:0:0"
  driver "ati"
  screen 1
  vendorname "ATI"
  option "MergedFB" "off"
EndSection
Section "screen" # 
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
EndSection
Section "monitor" # 
  identifier "monitor1"
  gamma 1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by tajmox on 2007-06-13
> **phollos said:**
> Hmm okay I had the exact same problem as you setting up my 1680x1050 resolution monitor. I remember being REALLY frustrated because my xorg file didn't match the available resolutions just like you're experiencing.

I can't for the life of me figure out *exactly* what I did though to fix it though! =(

There were only 2 things that I messed with to fix it if I remember correctly. I installed the fglrx driver for my ati card, and I updated my monitor from "generic monitor" to "Dell 2005FPW". I'm pretty sure that was what caused it to work all of a sudden because it automatically entered the resolutions I needed into my xorg.conf file. So I'd try updating your monitor information.

You just typed your monitor model name into the reconfigure script?

---

### Post by tajmox on 2007-06-13
Oh, also it is a Dell E1505.

Here is my Xorg.0.log:
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux max 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun 13 11:45:16 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
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
(II) PCI: 00:00:0: chip 8086,27a0 card 1028,01bd rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1028,01bd rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,27d6 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1028,01bd rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1028,01bd rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1028,01bd rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1028,01bd rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1028,01bd rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 1028,01bd rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,27c4 card 1028,01bd rev 01 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1028,01bd rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,7149 card 1028,2003 rev 00 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 14e4,170c card 1028,01af rev 02 class 02,00,00 hdr 00
(II) PCI: 03:01:0: chip 1180,0832 card 1028,01bd rev 00 class 0c,00,10 hdr 80
(II) PCI: 03:01:1: chip 1180,0822 card 1028,01bd rev 19 class 08,05,01 hdr 80
(II) PCI: 03:01:2: chip 1180,0843 card 1028,01bd rev 01 class 08,80,00 hdr 80
(II) PCI: 03:01:3: chip 1180,0592 card 1028,01bd rev 0a class 08,80,00 hdr 80
(II) PCI: 03:01:4: chip 1180,0852 card 1028,01bd rev 05 class 08,80,00 hdr 80
(II) PCI: 0b:00:0: chip 8086,4222 card 8086,1020 rev 02 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,12), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfd00000 - 0xdfefffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 11: bridge is at (0:28:0), (0,11,11), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 11 non-prefetchable memory range:
	[0] -1	0	0xdfc00000 - 0xdfcfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 12: bridge is at (0:28:3), (0,12,13), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 12 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 12 non-prefetchable memory range:
	[0] -1	0	0xdfa00000 - 0xdfbfffff (0x200000) MX[B]
(II) Bus 12 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd01fffff (0x200000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xdf900000 - 0xdf9fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc M52 [ATI Mobility Radeon X1300] rev 0, Mem @ 0xc0000000/28, 0xdfdf0000/16, I/O @ 0xee00/8
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
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.34.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.34g1                           
(II) ATI Proprietary Linux Driver Build Date: Feb 20 2007 11:49:19
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.34.1.1.2.3-driver-lnx-x86-x86_64-327152
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x7149) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[5] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[6] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[7] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[8] -1	0	0xdf9fd400 - 0xdf9fd4ff (0x100) MX[B]
	[9] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[10] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[11] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[12] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[13] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[18] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[19] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[20] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[21] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[24] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[25] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[26] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[27] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e6968
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[5] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[6] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[7] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[8] -1	0	0xdf9fd400 - 0xdf9fd4ff (0x100) MX[B]
	[9] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[10] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[11] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[12] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[13] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[21] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[22] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[27] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[28] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[29] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[30] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "ATI Mobility Radeon X1300" (Chipset = 0x7149)
(--) fglrx(0): (PciSubVendor = 0x1028, PciSubDevice = 0x2003)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xdfdf0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M52P
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.34.8
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 65536 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SEC  Model: 3250  Serial#: 0
(II) fglrx(0): Year: 2006  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) fglrx(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 119.2 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1052  v_sync_end 1058 v_blanking: 1080 v_border: 0
(II) fglrx(0):  CF264154P2
(II) fglrx(0):  (?HT}£Óÿ
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff004ca3503200000000
(II) fglrx(0): 	00100103802115780a87f594574f8c27
(II) fglrx(0): 	27505400000001010101010101010101
(II) fglrx(0): 	010101010101932e90a0601a1e403020
(II) fglrx(0): 	26004bcf100000190000000f00000000
(II) fglrx(0): 	00000000003cd2026400000000fe0043
(II) fglrx(0): 	463236340231353450320a20000000fe
(II) fglrx(0): 	00283f48547da3d3ff02010a20200055
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3.  5 power states available:
(II) fglrx(0):   1. 398/342MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 324/135MHz @ 60Hz [low voltage, enable sleep, thermal diode mode]
(II) fglrx(0):   3. 209/252MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   4. 392/252MHz @ 60Hz [enable sleep, thermal diode mode]
(II) fglrx(0):   5. 392/252MHz @ 60Hz [enable sleep]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 14 modes found for primary display.
(--) fglrx(0): Virtual size is 1680x1050 (pitch 0)
(**) fglrx(0): *Mode "1680x1050": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"  119.23  1680 1728 1760 1840  1050 1056 1058 1080 +hsync +vsync
(**) fglrx(0): *Mode "1280x720": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"  119.23  1280 1728 1760 1840  720 1056 1058 1080 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"  119.23  1024 1728 1760 1840  768 1056 1058 1080 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"  119.23  800 1728 1760 1840  600 1056 1058 1080 +hsync +vsync
(**) fglrx(0):  Default mode "1280x1024": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  119.23  1280 1728 1760 1840  1024 1056 1058 1080 +hsync +vsync
(**) fglrx(0):  Default mode "1152x864": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"  119.23  1152 1728 1760 1840  864 1056 1058 1080 +hsync +vsync
(**) fglrx(0):  Default mode "720x480": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"  119.23  720 1728 1760 1840  480 1056 1058 1080 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"  119.23  640 1728 1760 1840  480 1056 1058 1080 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"  119.23  640 1728 1760 1840  432 1056 1058 1080 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"  119.23  640 1728 1760 1840  400 1056 1058 1080 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"  119.23  512 1728 1760 1840  384 1056 1058 1080 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"  119.23  400 1728 1760 1840  300 1056 1058 1080 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"  119.23  320 1728 1760 1840  240 1056 1058 1080 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"  119.23  320 1728 1760 1840  200 1056 1058 1080 +hsync +vsync
(--) fglrx(0): Display dimensions: (330, 210) mm
(--) fglrx(0): DPI set to (129, 126)
(--) fglrx(0): Virtual size is 1680x1050 (pitch 1728)
(**) fglrx(0): *Mode "1680x1050": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"  119.23  1680 1728 1760 1840  1050 1056 1058 1080 +hsync +vsync
(**) fglrx(0): *Mode "1280x720": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"  119.23  1280 1728 1760 1840  720 1056 1058 1080 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"  119.23  1024 1728 1760 1840  768 1056 1058 1080 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"  119.23  800 1728 1760 1840  600 1056 1058 1080 +hsync +vsync
(**) fglrx(0):  Default mode "1280x1024": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  119.23  1280 1728 1760 1840  1024 1056 1058 1080 +hsync +vsync
(**) fglrx(0):  Default mode "1152x864": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"  119.23  1152 1728 1760 1840  864 1056 1058 1080 +hsync +vsync
(**) fglrx(0):  Default mode "720x480": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"  119.23  720 1728 1760 1840  480 1056 1058 1080 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"  119.23  640 1728 1760 1840  480 1056 1058 1080 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"  119.23  640 1728 1760 1840  432 1056 1058 1080 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"  119.23  640 1728 1760 1840  400 1056 1058 1080 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"  119.23  512 1728 1760 1840  384 1056 1058 1080 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"  119.23  400 1728 1760 1840  300 1056 1058 1080 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"  119.23  320 1728 1760 1840  240 1056 1058 1080 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 119.2 MHz (scaled from 0.0 MHz), 64.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"  119.23  320 1728 1760 1840  200 1056 1058 1080 +hsync +vsync
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
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(II) fglrx(0): [pcie] 126976 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[7] -1	0	0xdf9fd700 - 0xdf9fd7ff (0x100) MX[B]
	[8] -1	0	0xdf9fd600 - 0xdf9fd6ff (0x100) MX[B]
	[9] -1	0	0xdf9fd500 - 0xdf9fd5ff (0x100) MX[B]
	[10] -1	0	0xdf9fd400 - 0xdf9fd4ff (0x100) MX[B]
	[11] -1	0	0xdf9fd800 - 0xdf9fdfff (0x800) MX[B]
	[12] -1	0	0xdf9fe000 - 0xdf9fffff (0x2000) MX[B]
	[13] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[14] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[15] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[20] 0	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[24] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[25] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[26] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[27] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[30] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[31] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[32] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[33] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7bde000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.34.8
(II) fglrx(0):     Date: Feb 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.20-16-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x008f7000
(II) fglrx(0): FBMM initialized for area (0,0)-(1728,1360)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1728,1050) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1728 x 304
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		26 128x128 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Interrupt handler installed at IRQ 16.
(II) fglrx(0): Exposed events to the /proc interface
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
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
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
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
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
ProcXCloseDevice to close or not ?
```

---

### Post by Memocjro on 2007-06-19
```

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 84.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

```
This one is the section with problems. 

You should install xresprobe:
```
sudo apt-get install xresprobe
```
then do an xresprobe on the driver you need (in this example fglrx is the one with problems)
```
sudo xresprobe fglrx
```

You should get an output. I'll give mine for example
```
id: COMPAQ 7500
res: 1024x768 800x600 640x480
freq: 30-70 50-140
disptype: crt
```
**freq: x-y a-b** <- that's what is interesting for you

where:
**x-y** is the vaule for HorizSync
**a-b** is are the values for VertRefresh

Now you go in the above section and edit puting in your values, like i did for my example:
```
HorizSync    28.0 - 84.0
```
to
```
HorizSync    30-70
```

and 
```
VertRefresh    43.0 - 60.0
```
to
```
VertRefresh    50-140
```

---

### Post by tajmox on 2007-06-23
That sounds like a perfect solution, but sudo xresprobe fglrx returned this:

id: 
res: 
freq: 
disptype: lcd/lvds


I was so excited when I saw your reply...then so let down =(

---

