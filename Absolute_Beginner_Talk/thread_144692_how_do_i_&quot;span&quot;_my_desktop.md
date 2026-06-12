---
title: "how do i &quot;span&quot; my desktop?"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by chrluc on 2006-03-14
ok so I decided i need a larger desktop and I have an extra lcd so I read that it could be done. i guess first i need to know if i connect an lcd to my laptop ( the vga port in the back) can ths be done? I dont have a "special" video card but I was under the empression that on a laptop it was possible. so here is my xorg.conf 

sorry dont know how to put it into the thread fancy-like but here it is please let me know if i did something wrong.

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
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
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"S3 Inc. 86C270-294 Savage/IX-MV (Primary)"
	Driver		"savage"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	
EndSection

Section "Device"
	Identifier	"S3 Inc. 86C270-294 Savage/IX-MV (Secondary)"
	Driver		"savage"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"

EndSection

Section "Monitor"
	Identifier	"Generic Monitor (Primary)"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"Generic Monitor (Secondary)"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Primary Screen"
	Device		"S3 Inc. 86C270-294 Savage/IX-MV (Primary)"
	Monitor		"Generic Monitor (Primary)"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Secondary Screen"
	Device		"S3 Inc. 86C270-294 Savage/IX-MV (Secondary)"
	Monitor		"Generic Monitor (Secondary)"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerFlags"
 Option "Xinerama" "ON"
 EndSection
 

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Primary Screen" 0 0
	Screen 1	"Secondary Screen" RightOf "Primary Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


thanks all!

---

### Post by Pragmatist on 2006-03-15
Did you make the changes to your xorg.conf?  Have you tried using the two monitors yet to see if it works?  What happened?

---

### Post by chrluc on 2006-03-15
yes i made the changes, and when i connect two monitors i get the same deiplay x 2 or the same thing on both monitors. It still will not span across the two. Is there something i may be missing? do i have to activate the process.

---

### Post by Pragmatist on 2006-03-15
Ok, now I figured out to use the keyword (xinerama) in the ubuntu wiki.  These are the pages you want to read:

[https://wiki.ubuntu.com/XineramaHowTo?highlight=%28xinerama%29](https://wiki.ubuntu.com/XineramaHowTo?highlight=%28xinerama%29)
[https://wiki.ubuntu.com/XineramaMultipleMonitors?highlight=%28xinerama%29](https://wiki.ubuntu.com/XineramaMultipleMonitors?highlight=%28xinerama%29)
[https://wiki.ubuntu.com/XineramaSupport?highlight=%28xinerama%29](https://wiki.ubuntu.com/XineramaSupport?highlight=%28xinerama%29)

---

