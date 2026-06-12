---
title: "Video Resolution"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Sprakula on 2007-08-10
Hello, I am having a problem with getting Feisty to display the native resolution for my Viewsonic VX2025wm monitor,  the native resolution is 1680x1050.  I am running it off a EVGA Nvidia 8600gts.  I have done all the things that I could find to make the thing display correctly but to no avail.  The horizontal and vertical sync rates and such are correct, I have tried inputing all the resolutions for the monitor in, with 60 refresh rate and 75, and it still won't let me get past 800x600.  I've installed the latest driver from Nvidia.  The Nvidia console, though, will not let me choose any resolution other than "Auto" and this sets the monitor at 800x600, I did the reconfigure code thing to reset my xorg.conf file, and it somewhat worked, I am able to enable desktop effects, but it just won't let me change the resolution.  I have posted my Xorg.conf file below, as well as some pics of my nvidia console showing what it's doing.  If you have any pointers or help that would be great.  Thanks in advance!

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
	Option		"XkbModel"	"pc104"
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
	Identifier	"Nvidia 8600gts"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Viewsonic VX2025wm"
	Option		"DPMS"
	HorizSync	30,82
	VertRefresh	50,75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia 8600gts"
	Monitor		"Viewsonic VX2025wm"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050_60" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050_60" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050_60" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050_60" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050_60" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050_60" "1280x1024" "1024x768" "800x600" "640x480"
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

[IMG]http://x06.xanga.com/e5c82041d8368141011285/m103976224.png[/IMG]

[IMG]http://x1f.xanga.com/32b83a43d8368141011284/m103976223.png[/IMG]

[IMG]http://x07.xanga.com/65d80477d8366141011281/m103976220.png[/IMG]

---

### Post by splintercellguy on 2007-08-10
The xorg.conf file has the horiz/vsync values entered incorrectly. Shouldn't it be a dash instead of a comma?

---

### Post by Gary.M on 2007-08-10
How did you install the Nvidia drivers?

---

### Post by Sprakula on 2007-08-11
The Horizantal sync and Vertical refresh rates are separated by a comma, I tried separating them with a dash but it actually worked better with a comma.  The best resolution I could get when they were separated by a dash was 640x480, when I did it with a comma it went up to 800x600.  Kinda weird, I'm going to try it again with a dash today, but I don't think it'll work any better.

I installed the driver with Envy, then did the xconfig 'reconfigure' myself.

EDIT: I tried it again, the only thing that worked better was when it had a comma.  I tried 30-82, 30 - 82, 30.0-82.0, 30/80 (which crashed X), but to no avail.  If it is set with a - in it it gives me options of changing the resolution to 640x480 and below, if I put a comma in it there is only the Auto option for the resolution.

---

### Post by Sprakula on 2007-08-12
bump.

Any help is much appreciated

---

### Post by Steveway on 2007-08-12
> "1680x1050_60"
That doesn't look right.

---

### Post by Sprakula on 2007-08-13
I just reinstalled Feisty, am now using the vesa driver and almost everything is working perfectly.  I've got the resolution I want, the refresh rate I want, everything, the only thing I had to do was to manually put my Horiz/Vert rates in and the resolutions I wanted (Even though every time I did this with the Nvidia driver installed it didn't change anything, kept it at 640x480).  The only thing is I can't enable Desktop Effects, all I get is a white screen with my mouse, then after 30 seconds or so it reverts back to the normal desktop.  

I can't figure out why in the world the Nvidia drivers are not working on my system, I'm beginning to think that the drivers are not made, or do not work for my video card (Evga 8600gts) even though I got them through both Envy and directly off the Nvidia website.  I'm not sure if I should report this as a bug or not, maybe I'm missing something, but if anyone has any advice on maybe getting a better Nvidia driver or something.  The driver I manually installed off the Nvidia website was NVIDIA-Linux-x86-100.14.11-pkg1.run this is the driver it gave me when I selected "Graphics Driver-8 Series-Linux x86".  

I would still like to use an Nvidia driver if I could, but only if it works.  Any advice?

---

### Post by Hobo Joe on 2007-08-13
It may have something to do with how you installed it. But that's just a guess.

If you didn't use Envy, I'd recommend it. Check my sig for a link.

---

