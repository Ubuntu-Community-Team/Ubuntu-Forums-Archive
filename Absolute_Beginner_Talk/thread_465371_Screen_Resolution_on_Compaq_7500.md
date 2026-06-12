---
title: "Screen Resolution on Compaq 7500"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by karuptdata on 2007-06-05
Hi guys! Havent used Ubuntu in a very long time..and i have to admit im stumped on this one, ive read all of the howtos that i could find on this one to no avail. Basically my monitor supports higher that 1024*768 in fact its highest ratio is 1280*1024. Here is the output from lspci

```
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 02)
02:04.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)

```

And heres my xorg.conf
```
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
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
	Identifier	"Intel Corporation 82815 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"COMPAQ 7500"
	Option		"DPMS"
        HorizSync       30-70
        VertRefresh     50-140
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82815 CGC [Chipset Graphics Controller]"
	Monitor		"COMPAQ 7500"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

I did run sudo dpkg-reconfigure xserver-xorg and set the proper screen resolution however upon reboot of course i just get a black screen. I also tried to follow these intructions located [here]("http://ubuntuforums.org/showthread.php?t=351647&highlight=painless+intel") for Intel Video chipsets with no luck still. Any input on this is greatly appreciated

Regards,

Karuptdata

---

### Post by Rocket2DMn on 2007-06-05
You can manually add the higher resolutions for each depth in the Screen section of xorg, then restart X.

---

### Post by karuptdata on 2007-06-06
Awesome i knew it had to be something simple that i was missing. Thanks alot my friend you rock :D

---

### Post by mmendez on 2007-06-06
hey did you get your wireless card working? if so mind telling me how? I have one too and its recognized but no driver so I have been using ethernet and well I wanted to get rid of one extra wire

---

### Post by frenchn00b on 2008-02-16
> **karuptdata said:**
> Hi guys! Havent used Ubuntu in a very long time..and i have to admit im stumped on this one, ive read all of the howtos that i could find on this one to no avail. Basically my monitor supports higher that 1024*768 in fact its highest ratio is 1280*1024. Here is the output from lspci

```
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 02)
02:04.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)

```


Karuptdata


Hello  Karuptdata, 
Did you now managed to get the GLX working ?
(I would like to play mupen64 actually with it)
It was a quite fast machine the compaq

---

