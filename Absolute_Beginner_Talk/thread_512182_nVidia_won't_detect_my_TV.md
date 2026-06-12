---
title: "nVidia won't detect my TV"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by samihuu on 2007-07-28
Hi there.

Tried to find info on this subject but it hasn't helped so far.

I have a nVidia 6600 card that I want to connect to both my CRT monitor and my Widescreen CRT TV.  Works perfectly with the monitor but it won't detect the TV. From startup of the PC I have picture on the TV, but when xorg starts the signal is lost. 

xorg.conf:

##################################################################
#                      X Configuration File                      #
#         Created by YanC42 0.0.9 (29-07-2007 02:32:10)          #
#               (c) 2002-2005 by Sebastian J. Wolf               #
#        Licensed under GNU General Public License (GPL)         #
#     [http://yanc.ygriega.de/](http://yanc.ygriega.de/) - [http://yanc.sourceforge.net/](http://yanc.sourceforge.net/)     #
##################################################################

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
	Option		"XkbLayout"	"se"
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
	Identifier	"nVidia Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	Busid		"PCI:2:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"False"
	Option "TwinView" "1"
	Option "MetaModes" 	"1600x1200,1600x1200;1280x1024,1280x1024;1280x960,1280x960;1152x864,1152x864;1024x768,1024x768;800x600,800x600;640x480,640x480"
	Option "TwinViewOrientation" "RightOf"
	Option "SecondMonitorHorizSync" ""
	Option "SecondMonitorVertRefresh" ""
	Option "TVStandard" "PAL-B"
	Option "RenderAccel"
	Option     "AllowGLXWithComposite"
EndSection


Section "Monitor"
	Identifier	"NEC FE950+"
	Option		"DPMS"
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce 6600 GT]"
	Monitor		"NEC FE950+"
	Defaultdepth	24
	Option	"RenderAccel" "true"
	SubSection "Display"
		Depth	1
		Modes		"1600x1200"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1600x1200"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1600x1200"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1600x1200"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1600x1200"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1600x1200"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
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
	Screen	0	"Default Screen" 0 0
EndSection


Section "DRI"
	Mode	0666
EndSection


Thanks for any help I can get.

---

### Post by ICUR2Ys on 2007-07-28
I am not very techy and I don't know what is involved in setting up the tv.  I have nvidia and I use twinview to run dual monitors.  Is there a reason that you are not running twinview?

---

### Post by samihuu on 2007-07-29
Well, Twinview is what I want to go for. I believe I have set this up in xorg.conf, but the problem is that it won't even detect the TV in X.

---

### Post by ICUR2Ys on 2007-07-29
Since your are not in dual mode it won't show.

gksudo nvidia-settings

Enter the above command and see if you have nvidia-settings installed,  If you do enable your tv and configure it.  If you can save the configuration to the xorg.conf file.  I wasn't able to, always got an error.  I was able to preview before saving so I copied the stuff about twinview and updated manually.  However on my other computer I didn't have the preview option.

Good luck

Edit:  Sorry your twinview is in a different location in the file than mine and I didn't see it.  I guess I can't help.

Edit again:  Just in case this may help it is my a portion of my file.

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1680x1050 +1280+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by samihuu on 2007-08-06
Thanks for the reply. Been away for a week on vacation so I didn't have time to look at it. I used nvidia-settings successfully and managed to set up the TV. Thanks for the help. :D

At the moment I'm just not sure how to setup a widescreen resolution on the TV. Any idea on this?

---

### Post by ICUR2Ys on 2007-08-06
I think your options are limited.  I first set up the recommended resolutions on my nineteen inch monitor and my 22 widescreen monitor.  However, I then couldn't see the bottom panel on the nineteen inch monitor.  So I played around in nvidia settings with the resolution on the wide screen until I got one that would work on it.  It is acceptable right now but it would be better if I get another widescreen monitor with the same resolution.  My monitor would not take some of the resolutions.  That is why I think your options might be limited.

Good luck.

---

