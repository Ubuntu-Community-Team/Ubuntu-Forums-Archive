---
title: "[SOLVED] Compiz fusion Problem"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Donnie Darko on 2007-11-01
I've been away from ubuntu from a while, and rediscovered my love of it. I've seen this new compiz fusion, and I installed it. Whenever I try to enable desktop effects it says they cannot be enabled. I'm running a compaq presario SR1750NX, with gutsy, 1gb ram, and 2.3ghz amd athalon processors and a  ATI radion express 200 graphic card. What could be wrong here?

---

### Post by llamakc on 2007-11-01
Post your /etc/X11/xorg.conf file.

---

### Post by Arthur Archnix on 2007-11-01
Yes, the xorg.conf file is useful. So too is output of
```
lspci | grep Display
```
and
```
glxinfo | grep render
```

---

### Post by Donnie Darko on 2007-11-02
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
	Identifier	"ATI Technologies Inc RS480 [Radeon Xpress 200G Series]"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"HP vs17"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS480 [Radeon Xpress 200G Series]"
	Monitor		"HP vs17"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"

glxinfo
 glxinfo | grep render
Warning, xpress200 detected.
direct rendering: Yes
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 NO-TCL

The lspci one isn't working for me.

---

### Post by JustinAllen on 2007-11-02
Heya Donnie.  I've got the same exact vid card you have.  Here's what I did to get it working.

1.  Go into System > Administration > Restricted Drivers Manager.  Once that pulls up, you should see your vid card there.  Enable and install the restricted ATI drivers.

2.  Reboot.

3.  Install xserver-xgl via Synaptic or apt-get.

4.  Reboot (not sure if it's necessary, but i did it anyway)

5.  Enable desktop effects.

6.  Install compizconfig-settings-manager

Once the CCSM is installed, it will add an entry in System > Preferences

That was all I had to do to get it running after a fresh install of Gutsy.

---

### Post by Donnie Darko on 2007-11-03
Thank you so much! I ran it and it's going perfectly. Now to learn the keystrokes!

---

