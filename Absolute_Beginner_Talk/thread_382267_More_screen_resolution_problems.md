---
title: "More screen resolution problems"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Native Dialect on 2007-03-11
Okay so i've attempted the DIY approach for the past two hours, and now I figure i'll turn for help. As Confucious once stated "tis better to ask a question and be a fool for five minutes, than to ask nothing and remain a fool forever." So my problem is, I am trying to use my onboard graphics card (Intel 8245G Extreme Graphics). A crappy card yes, but I am entirely uninterested in playing games (at least powerful ones). Well as I am sad to see, there is no easy way to install graphics drivers for Linux. Without the simplicity of an self extracting executable, which is so common in Windows, I am just utterly lost. I tried downloading the zip file from Intel, but the install.sh file never runs. It asks if I want to run it, I click run, I get nothing. It asks if I want to run it in the terminal (not that I even know how to open the terminal or what the terminal is) and it still won't run. I try to search for some basic driver using the Synaptic manager and I can find nothing (I even have it set to Universe). So what do I have to do, so I can install some drivers, so I can stop looking at a screen size of 640x480?

---

### Post by Native Dialect on 2007-03-11
somebody please help. it is difficult to manage the computer when I can't even see the bottom of certain windows. I can't even resize the windows so i can get scroll bars. The menus just go off screen, and what I can't see remains so. I need some guidance.

---

### Post by alienexplorers on 2007-03-12
Post your xorg.con file here.  Use terminal from Applications>Terminal.

terminator@terminator-desktop:~$ cat /etc/X11/xorg.conf

---

### Post by Native Dialect on 2007-03-12
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
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"SDM-M51"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"SDM-M51"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"720x400" "640x480" "640x400"
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
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Najand on 2007-03-12
Run:```

sudo dpkg-reconfigure xserver-xorg

```
Push enter until you reach to the page with: "Video modes to be used by the X server"
Select your desirable resolutions using TAB and SPACE bottons(Caution: Don't select higher resolution than the one you want to use")
Select OK and push enter until you reach its end.
After you saw the terminal default page again, Push Ctrl+Alt+Backspace to restart X. Login and you would be done.

---

### Post by tiagobugarin on 2007-03-12
Same problem here.
I got it solved this way.

1- at BIOS i set my graphics card to onchip (i have this option and it was set to agp)
2- at BIOS i set my shared memory (main memory with onboard graphics card) to 8mb (this is the maximum i can get here; it was set to 1mb)
3- returned my /etc/default/915resolution file to the default state (auto and no other setup made)
4- i set my /etc/X11/xorg.conf to the original state (i810 driver, 24bits and 1280x1024)

it is now running correctly for me.

one thing i noted is that the real problem was the ammount of memory for my allocated for my onboard card.
- the graphical boot loading wasn't showing up
- extremely low grub (?!?!?)
- windows xp running fine
- X resolution 640x480@60Hz

after the memory changes in BIOS every thing changed (except windows still running fine)
- graphical boot loading
- fast grub
- X resolution 1280x1024@75Hz

---

### Post by Native Dialect on 2007-03-13
Thank you both for your help. I was finally able to get my resolution set to 1024x768. I appreciate it.

---

