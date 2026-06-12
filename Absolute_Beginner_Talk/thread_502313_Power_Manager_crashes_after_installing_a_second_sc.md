---
title: "Power Manager crashes after installing a second screen."
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by tikey on 2007-07-16
Hi!

Some time ago i bought a second monitor for my laptop (iiyama ProLite E2200WSV) and after having some trouble to set it up in a way that I liked i finally got it.
Now I have another problem: Whenever I start the computer the Power Manager crashes and it shows me the following Backtrace:

```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1210378032 (LWP 5749)]
(no debugging symbols found)
... I keep some of them ...
(no debugging symbols found)
[KCrash handler]
#6  0xb68b9454 in ?? () from /usr/lib/libXrandr.so.2
#7  0x0001afd1 in ?? ()
#8  0x0859d030 in ?? ()
#9  0x00000048 in ?? ()
#10 0xb6b84b2c in ?? () from /usr/lib/libX11.so.6
#11 0x00000000 in ?? ()

```

Also, when I go to the system settings and try to set the Monitor & Screen settings it crashes and systemsettings gives me the following bactrace:

```

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
... I'm gonna save you all these again ...
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1232619296 (LWP 10820)]
(no debugging symbols found)
... and again ...
(no debugging symbols found)
[KCrash handler]
#6  0xb6a61454 in ?? () from /usr/lib/libXrandr.so.2
#7  0x000025e9 in ?? ()
#8  0x08351a18 in ?? ()
#9  0x00000048 in ?? ()
#10 0xb69d1b2c in ?? () from /usr/lib/libX11.so.6
#11 0x00000000 in ?? ()

```

All this happens since I changed my xorg.conf to:
```
Section "Files"
  FontPath "/usr/share/fonts/X11/misc"
  FontPath "/usr/share/fonts/X11/cyrillic"
  FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
  FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
  FontPath "/usr/share/fonts/X11/Type1"
  FontPath "/usr/share/fonts/X11/100dpi"
  FontPath "/usr/share/fonts/X11/75dpi"
  # path to defoma fonts
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "record"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc105"
  option "XkbLayout" "us"
  option "XkbVariant" "intl1"
  option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ImPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Identifier "Synaptics Touchpad"
  Driver "synaptics"
  option "SendCoreEvents" "true"
  option "Device" "/dev/psaux"
  option "Protocol" "auto-dev"
  option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  option "Device" "/dev/input/wacom"
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  option "Device" "/dev/input/wacom"
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/input/wacom"
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	identifier "0 ATI Radeon 9700"
	boardname "ati"
	busid "PCI:1:0:0"
	driver "ati"
	screen 0
	Option "DDCMode" "True"
	Option "MonitorLayout" "LVDS, CRT"
EndSection

Section "Device"
	identifier "1 ATI Radeon 9700"
	boardname "ati"
	busid "PCI:1:0:0"
	driver "ati"
	screen 1
	Option "DDCMode" "True"
	Option "MonitorLayout" "LVDS, CRT"
EndSection

Section "Monitor"
	Identifier	"Laptop LCD"
	Option		"DPMS"
	HorizSync	28-50
	VertRefresh	43-75
EndSection


Section "Monitor"
	identifier "extern LCD"
	vendorname "Generic"
	modelname "Flat Panel 1680x1050"
	HorizSync 31.5-90
	VertRefresh 60
# use this modeline for the iiyama E2200WSV (or might there be a better one???)
	modeline "1680x1050" 146.250 1680 1784 1960 2240 1050 1053 1059 1089 -hsync +vsync
	modeline "1680x1050_1" 146.2 1680 1784 1960 2240 1050 1053 1059 1089
  gamma 1.0
EndSection

Section "Screen"
	Identifier	"Main Screen"
	Device		"0 ATI Radeon 9700"
	Monitor		"Laptop LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"1 ATI Radeon 9700"
	Monitor		"extern LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1680x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Main Screen"
	Screen		"Second Screen" LeftOf "Main Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"stylus" "SendCoreEvents"
	InputDevice	"cursor" "SendCoreEvents"
	InputDevice	"eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerFlags"
	Option	"Xinerama" "true"
EndSection

Section "DRI"
  Mode 0666
EndSection

```

Another error that I get happens whenever I start kate or some other programs from konsole:
```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```
I never fixed this one b/c it didn't have any influence on my work. Everything was just working fine. Now I thought this one might be related to the xorg.conf, too. So I posted it.

If anyone knows s/th which could help I would greatly appreciate if you let me know about it!

thanks

---

### Post by Al3xK3aton on 2007-07-17
I have a feeling you could fix the problem by removing the second monitor.

---

### Post by tikey on 2007-07-17
Well, I really want to keep the second monitor. I like to work with two of them!

---

### Post by tikey on 2007-07-27
Does anyone have an idea?

---

### Post by tikey on 2007-08-24
bump

---

