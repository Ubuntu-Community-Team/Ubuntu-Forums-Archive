---
title: "Getting the proper resolution with an ATI card"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by akschnare on 2007-06-06
Hey there, I'm fairly new to Linux and I have a question about the ATI drivers. Can I use the one that comes with Feisty or will I need the other one to run certain programs? 

I have a Dell monitor with a resolution of 1920 x 1200 but Ubuntu only lets me go as high as 1600 or something close to that. I liked the desktop effects that come with Feisty and was using them until I installed the other driver. Now they won't work, but I have the proper resolution. I downloaded and installed Beryl once I got the new drivers, but it seemed to run a lot slower. I'm running an old Athalon 2500+ so I know not to expect the best performance with the desktop effects, but the standard one that comes with Feisty worked really well.

I guess I just want to know how to get my standard drivers to display the higher resolution. And I'd like to know if the drivers will be good for me, or if I have to use the other drivers.

Thanks a lot.

---

### Post by Inxsible on 2007-06-06
can you post your xorg.conf
```
gksudo gedit /etc/X11/xorg.conf
```
 
Make sure the X in X11 is uppercase

---

### Post by Inxsible on 2007-06-06
Actually, you can edit that file and add the higher resolutions that you need in the section called screens. Add them before a list of all the resolutions that are listed there. 
 
There might be multiple lines, where you would have to do this.

---

### Post by akschnare on 2007-06-06
I can't post it now because I'm at work. But I will when I get home, and I'll try editing in the resolutions. Thanks.

---

### Post by kelvin spratt on 2007-06-06
i use an ATI graphics card with no problems with all the effects straight from the box i'm lucky i suppose, but if they worked before you changed them then go back. i also use a Dell monitor and find 1600x1200x75 is perfect for me in XP the same card with catilist drivers was best at 1275x1040x75hz with my 19" screen

---

### Post by akschnare on 2007-06-06
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
	Identifier	"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Driver		"ati"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL 2405FPW"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Monitor		"DELL 2405FPW"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
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

### Post by akschnare on 2007-06-06
There's my config file, I just can't edit the resolution to  1920 x 1200 and get it to work.

---

