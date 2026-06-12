---
title: "beryl feisty on ibook g3 dual usb"
date: 2007-05-27
forum: Apple PPC Users
---

### Post by jah on 2007-05-27
I have been having great trouble getting this running, even though prima face it should seem to work. If i type "glxinfo" I can see "direct rendering: yes" which surely means that my system is capable of desktop effects, and that i'm running the right driver.

however after installing beryl, and then starting "beryl-manager", problems arise. At first it looks like it is going to work, but then all the title bars disappear, and within 5 seconds the X server has restarted and you have to log in again.

Has anyone successfully got beryl/compiz working on a g3 ibook?? if so i would be eternally greatful if you could show me how...

thanks

---

### Post by luciferin on 2007-05-27
I just installed Fiesty last night on my dual USB G3 and Beryl worked fine right off the bat..  First just make sure that you have all the latest updates installed.  If it's still not working then try enabling the "desktop effects" option that's in Ubuntu by default, if that works then we'll at least know it's a problem with your Beryl install.

Oh, one last thing, try running "beryl" from the command line to launch it and post the error here.

---

### Post by jah on 2007-05-27
thanks for your reply!

My fiesty installation is up to date. If i enable 'Desktop Effects', it attempts to activate them, however initially the title bars disappear and then after about 5 seconds X restarts automatically.

If i run 'beryl' from the terminal, it runs some 'tests'(?) within the terminal, and then proceeds to load beryl, however the same thing happens - after about 5 seconds X restarts. I can't post the error because there wasn't one.

I did manage to get beryl half working by following the instructions [**here**]("http://http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon"). However shouldn't it work 'out of the box' without tinkering with xorg?

My xorg.conf is here: (i don't know why but it says i have a radeon 9000, when i actually have a 7500. that was one of the things i changed when i was editing the xorg.conf...)

Thanks again.

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"type1"
	Load	"vbe"
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
	Option		"Protocol"		"ExplorerPS/2"
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
	Option 		"SHMConfig"		"true"
	Option		"VertEdgeScroll"	"1"
	Option		"LeftEdge"		"80"
	Option		"TopEdge"		"80"
	Option		"RightEdge"		"850"
	Option		"BottomEdge"		"560"
	
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
	Option		"DRI"			"true"
	Option		"ColorTiling"		"on"
	Option		"EnablePageFlip"	"true"
## Some may experience very poor performance without hashing the following line.
	Option		"AccelMethod"		"EXA"
## If above is hashed, change the following to "XAANoOffscreenPixmaps"
	Option		"EXANoOffscreenPixmaps"
	Option		"RenderAccel"		"true"
#Option "AGPMode" "x" <- x may be 1, 2, 4, or 8 depending on your system
	Option		"AGPFastWrite"		"on"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by tcrroadie on 2007-05-28
Hi jah,

I have an ibook G4 that I have successfully been able to get Beryl working on.  Lets first try cleaning up your xorg.conf file and see what happens.  First backup your xorg.conf if you have not done so all ready. 

```
sudo cp xorg.conf xorg.conf.old
```

Change your Section "Devise" from this 

```
Section "Device"
Identifier "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
Driver "ati"
BusID "PCI:0:16:0"
Option "UseFBDev" "true"
Option "DRI" "true"
Option "ColorTiling" "on"
Option "EnablePageFlip" "true"
## Some may experience very poor performance without hashing the following line.
Option "AccelMethod" "EXA"
## If above is hashed, change the following to "XAANoOffscreenPixmaps"
Option "EXANoOffscreenPixmaps"
Option "RenderAccel" "true"
#Option "AGPMode" "x" <- x may be 1, 2, 4, or 8 depending on your system
Option "AGPFastWrite" "on"
EndSection
```

To this

```
Section "Device"
Identifier "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
Driver "ati"
BusID "PCI:0:16:0"
Option "UseFBDev" "true"
EndSection
```

Now start beryl
```

beryl-manager
```

If you still have problems, try editing your xorg.conf file again and change the driver used from "ati" to "radeon" under Section "Device" and try to restart beryl again.

```
Driver "radeon"
```

Please post back and let us know how you are doing.

---

