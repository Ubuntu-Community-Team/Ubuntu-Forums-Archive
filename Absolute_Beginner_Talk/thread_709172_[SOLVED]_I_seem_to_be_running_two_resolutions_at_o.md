---
title: "[SOLVED] I seem to be running two resolutions at once for some reason"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by kudahl on 2008-02-27
Hi' there

After installing ubuntu I'm having some resolution problems...

I managed to get ubuntu to run my widescreen resolution of 1680*1050, but it seems like ubuntu is now running both the old resolution and the new resolution at the same time?!

This becomes a problem especially when running video or anything else that requires full screen...

I've taken a screenshot that i've attached....Now, as you can see there is a black 'bar' at the buttom and on the right side of the screen. This 'bar' is not visible when I take the screenshot, but only emerges after having saved the screenshot-file. It is as if the old resolution is placed on top of the new and larger resolution.

Is anyone capable of giving me some ideas for sovling this problem

Thanks in advance

kudahl

---

### Post by jordanmthomas on 2008-02-27
You forgot the attachment.  :|

---

### Post by kudahl on 2008-02-27
indeed...

---

### Post by kudahl on 2008-02-27
I will also paste my xorg.conf here:


Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"MaxTapTime"		"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1680x1050"
	Horizsync	31.5-65.5
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1680	1050
		Modes		"1280x800@60"	"1440x900@60"	"1280x720@60"	"1600x1024@60"	"1280x768@60"	"1680x1050@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"dbe"
	Load		"v4l"
EndSection
Section "Extensions"
	Option		"Composite"	"on"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by jordanmthomas on 2008-02-27
```
Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
Defaultdepth 24
SubSection "Display"
Depth 24
[COLOR="Red"]Virtual 1680 1050[/COLOR]
Modes "1280x800@60" "1440x900@60" "1280x720@60" "1600x1024@60" "1280x768@60" "1680x1050@60" "800x600@60" "800x600@56"
EndSubSection
EndSection
```

If you're comfortable with being able to revert the change on a command line, what happens if you move that resolution that you have listed as "Virtual" into your "Modes"?  

```
Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
Defaultdepth 24
SubSection "Display"
Depth 24
Modes[COLOR="Red"] "1650x1050@60"[/COLOR] "1280x800@60" "1440x900@60" "1280x720@60" "1600x1024@60" "1280x768@60" "1680x1050@60" "800x600@60" "800x600@56"
EndSubSection
EndSection
```

---

### Post by steveneddy on 2008-02-27
Make these lines look like this:

```

# Virtual 1680 1050
Modes "1680x1050@60" "1280x800@60" "1440x900@60" "1280x720@60" "1600x1024@60" "1280x768@60" "1680x1050@60" "800x600@60" "800x600@56"

```

And see if this helps.

EDIT:

Dang - beat me to it.

---

### Post by kudahl on 2008-02-27
yay, it worked perfectly.

Thanks to you both

kudahl

---

### Post by thisismalhotra on 2008-02-27
can you make the thred solved now please?? I will help other folks around here

---

### Post by steveneddy on 2008-02-28
And hit the "Thanks" buttons, please.

Thanks.

---

### Post by jordanmthomas on 2008-02-29
> **steveneddy said:**
> And hit the "Thanks" buttons, please.

Thanks.

Didn't he already say thanks?  Asking for people to click the Thanks button is just low down.

---

