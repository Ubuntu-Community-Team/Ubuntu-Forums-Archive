---
title: "Ctrl Alt F1(~6) do not work once logged in"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by losttale on 2007-06-01
Hey all,
I just upgraded to fiesty from edgy, but have been having this problem since after installing tpb on edgy.  I have a thinkpad t41.  Anyway, after installing tpb on ubuntu, ctrl alt f1-f7 (ie, my console xserver switcher) stopped working once logged in.  When i am at the login window, console mode works fine and I can go back and forth between gui world and console world.  But after I log in, these hot keys stop working and it's a little frustrating b/c i have to toy with my video card a lot (see: radeon 9000 mobility ha ha ha...).  The only way I can work in console mode now is to log out, then ctrl alt f1, then log back into the console and work that way.  then to get back to gui, I ctrl alt f7 and then log back into gnome.  What's wrong here?  I have reconfigured xorg a few times and it's possible I chose the wrong keyboard layout (so my f keys aren't f keys anymore...?), but it seems unlikely since a=a, b=b, c=c as you can see here now.

Thanks for any help!  Below is my current xorg.conf (it may have other problems I don't know about too, so feel free to critize my xorg configuration skills ;)):

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
	Load "GLcore"
	Load "i2c"
	Load "bitmap"
	Load "ddc"
	Load "dri"
	Load "extmod"
	Load "freetype"
	Load "glx"
	Load "int10"
	Load "type1"
	Load "vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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

Section "Device"
	Identifier "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
	Driver "ati"
	Screen 0
	BusID "PCI:1:0:0"
	Option "DRI" "true"
	Option "ColorTilling" "on"
	Option "EnablePageFlip" "true"
	Option "AccelMethode" "EXA"
	Option "XAANoOffscreenPixmaps" "true"
	Option "RenderAccel" "true"
	Option "AGPMode" "8"
	Option "AGPFastWrite" "on"
EndSection


Section "Monitor"
	Identifier	"Laptop Monitor"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
	Monitor		"Laptop Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "false"
EndSection

---

### Post by ajmorris on 2007-06-17
Hi,
what keyboard layout is selected in system >> preferences >> Keyboard?

---

### Post by dvo on 2007-12-21
After setting the wrong keyboard layout using xmodmap, I had the same problem.
One way to solve it was to restore the default layout, e.g. 
```
setxkbmap -layout us
```

---

