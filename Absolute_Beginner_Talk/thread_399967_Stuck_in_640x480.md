---
title: "Stuck in 640x480"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by FelisSchrodingeris on 2007-04-03
I've just upgraded to feisty. Everything else looks fine except the resolution (of course, I want to give compiz a try) 

The problem is simple: "System -> Prefs -> Screen Resolution" can only give me 640x480, and my xorg.conf tells me I could go up to 1440xsomething. I also ran the xserver-xorg config program in the terminal, to no avail: it still tells me I can go up to 1440xsomething. 

The problem must reside either somewhere else in xorg.conf or by linking to the "screen resolution" program. Here's my xorg.conf

> 
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
	Identifier	"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"1772ED"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"1772ED"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
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

---

### Post by kc5hwb on 2007-04-03
This question gets asked alot.  I now I get to ANSWER a question instead of asking one!  :) 

Check this thread that I made a while back...the instructions here in here.  Quick and simple and works perfectly.
[http://www.ubuntuforums.org/showthread.php?t=211811](http://www.ubuntuforums.org/showthread.php?t=211811)

---

### Post by FelisSchrodingeris on 2007-04-03
Well, I figured it out while I was waiting. It had to do with running the xserver-xconf app without running GDM. I figured I could run the app in the terminal and restart the GUI afterwards: not so. You may want to write that explicitly in that thread, BTW.

Thanks anyways, though, any help is always gladly appreciated.

---

