---
title: "New user problem"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by burt_57 on 2007-06-23
I have been having lots of problem when I try to make some changes
to Ubuntu Ultimate.
And when I do, I can not get back to my desktop after booting,
Well...I have found the link below and I give it a try.no once but 3 time to see
if I could rescue my desktop ......well it work just fine for me ;)
I did print the instruction before doing anything ,now it is in my Ubuntu Book.

go there   [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by netyire on 2007-06-24
Hmm, what changes did you try to make? Perhaps the xorg.conf file is the source of the problems. Do post /etc/X11/xorg.conf and let me take a look.

---

### Post by burt_57 on 2007-06-24
> **netyire said:**
> Hmm, what changes did you try to make? Perhaps the xorg.conf file is the source of the problems. Do post /etc/X11/xorg.conf and let me take a look.
My problem WAS  with my video drivers... but now everything is fine.
Ty for wanting to help.
In an other post somewhere I have mention a link where you can fix the problem .
It is well written and now I have made a copy of the step to take 
at the black scree of death .
go there   [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by burt_57 on 2007-06-24
here is my xconfSection 

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"nVidia Corporation G70 [GeForce 7600 GT]"
	Driver		"nvidia"
	Busid		"PCI:4:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Philips 170S"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 GT]"
	Monitor		"Philips 170S"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

