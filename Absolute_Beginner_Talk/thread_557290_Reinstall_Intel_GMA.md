---
title: "Reinstall Intel GMA?"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by tgvail on 2007-09-22
Hi everyone--

I have been running Feisty for a while now just fine, using the default desktop effects (compiz) that comes with this distribution. I tried to install beryl, and it worked for a couple of minutes, then everything started crashing, so I uninstalled it. Unfortunately, now none of my more advanced graphics will work, including the old desktop effects, games in wine that used to work, etc (I think opengl is gone, but I really do not know).

Does anyone know how I can reinstall what I need, or restore things back to default? I have an intel GMA 950.

---

### Post by Jeroen Vernooij on 2007-09-22
Hi,
It looks like your xorg.conf file is messed up since Beryl.

Best you can do is reboot in recovery mode (or logout, and login into a terminal session), 
and run a 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

It asks a lot of questions, if you don't know the answer, just press enter.

---

### Post by tgvail on 2007-09-22
Thanks for the quick reply!

Unfortunately, that did not work...do you have any other suggestions?

---

### Post by Jeroen Vernooij on 2007-09-22
Strange..

Please open a terminal (applications-> accessories -> terminal)
and type:
```
glxinfo | grep direct
```

and post the output here.

---

### Post by tgvail on 2007-09-22
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by Jeroen Vernooij on 2007-09-22
Ehm you think that opengl is missing, you can easily verify that by processing this command:
```
sudo apt-get install ubuntu-desktop ubuntu-minimal ubuntu-standard
```
If nothing installs, you have all the ubuntu packages so opengl is installed.

But I don't think that is the problem here.
I still think your xorg.conf file is messed up,
so maybe you can post it here.
It is located in the folder: /etc/X11

---

### Post by tgvail on 2007-09-22
I did that install and something was actually installed, but it did not fix the problem. So here is my xorg file. It is posted from after the big commented part on top.

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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Jeroen Vernooij on 2007-09-22
that file looks a lot like mine, but you still don't have direct rendering, which is required for 3d and opengl.

I don't know for sure, but dpkg-reconfigure xserver-xorg always brings back direct rendering on GMA950, but you said you already did that.

The driver you are running is called xserver-xorg-video-i810
You can try to reinstall it (search for it in Synaptic, and reinstall)

Otherwise I don't know any solutions; maybe you can post this thread in General Help since this isn't a beginner question.

---

### Post by tgvail on 2007-09-22
> **Jeroen Vernooij said:**
> 
Otherwise I don't know any solutions; maybe you can post this thread in General Help since this isn't a beginner question.

okay, I'll try that

thanks

---

