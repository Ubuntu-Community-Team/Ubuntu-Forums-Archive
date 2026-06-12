---
title: "ubuntu 7.10 black screen on eMac G4"
date: 2008-02-12
forum: Apple PPC Users
---

### Post by mic159 on 2008-02-12
I am trying to install ubuntu 7.10 on a eMac G4 (1.25Ghz)
i have tried all the vert, horizontal refresh rates i could find for an emac, but they make no diffrence wahtsoever.

when it boots, it shows the loading screen perfectally (the orange progress bar), and when it gets to the end, the screen goes black and it makes the startup sound and the cd keeps going like normal. It seems like it boots like it should, the only problem is i cant see anything!

i have tried diffrent refresh/sync rates and the video=ofonly, but they make no diffrence whatsoever.

has anyone got it working on a G4 emac??

Im using Ubuntu 7.10 desktop powerpc ISO

---

### Post by stream303 on 2008-02-13
From what I've heard, Feisty is your best bet for the eMac and possibly the mini in tough cases.  Seems like eMac owners get gray hairs with Gutsy. :)

If you want to run that, I'd suggest the "alternate" install image burnt at a low speed, and you may want to take a look at this - it has a good comment about disabling dri.  I don't think I've heard of a successful Gutsy install on an eMac.  Anyone?

[http://crowetech.wordpress.com/2007/04/14/ubuntu-704-beta-on-an-emac-part-1-installation/](http://crowetech.wordpress.com/2007/04/14/ubuntu-704-beta-on-an-emac-part-1-installation/)

Here's a link where you can grab Feisty

[http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/)

---

### Post by oswaldkelso on 2008-02-13
heres my emac xorg.conf if its any use to you 

EDIT: its from debian testing but  I dont think its change.

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/X11R6/lib/X11/fonts/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/X11R6/lib/X11/fonts/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/X11R6/lib/X11/fonts/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/X11R6/lib/X11/fonts/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/usr/X11R6/lib/X11/fonts/75dpi"
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
	Load    "dbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:lwin_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"iMac"
	Option		"DPMS"
	HorizSync	71-73
	VertRefresh	70-140
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
	Monitor		"iMac"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x960" "1152x870" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x960" "1152x870" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x960" "1152x870" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x960" "1152x870" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x960" "1152x870" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x960" "1152x870" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by stream303 on 2008-02-13
> **oswaldkelso said:**
> heres my emac xorg.conf if its any use to you 

That's great.  I think this would work very well in Feisty.  As I learned with my G5 iMac, Gutsy and Hardy tend to outsmart the most common xorg "fixes" and leave you with something undesirable, or even prevent it from working.

So in tough cases, maybe start with Feisty and go from there if you dare. :)

---

