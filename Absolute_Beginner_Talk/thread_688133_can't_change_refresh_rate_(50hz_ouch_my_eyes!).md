---
title: "can't change refresh rate (50hz ouch my eyes!)"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by lnlds on 2008-02-05
I checked in my xorg.conf files and all the settings say @60 but when i look at resolution or at screens and graphics it shows 1400x1050 @50hz.. My eyes have been getting really tired really quickly and looking at the screen really gives me a headache.
I have a thinkpad t42 with a radeon 7500

Section "Files"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1400x1050"
	Horizsync	31.5-65.5
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Generic Monitor"
	Defaultdepth	16
	SubSection "Display"
		Depth	16
		Virtual	1400	1050
		Modes		"1280x1024@60"	"1400x1050@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #    
	Identifier	"device1"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	1
	Option		"MergedFB"	"off"
EndSection
Section "screen" #    
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	16
	Monitor		"monitor1"
	SubSection "Display"
		Depth	16
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #    
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by lnlds on 2008-02-05
no one? maybe i'll try to get some sleep and hope its me? and the true refresh rate is 60hz?

---

### Post by hyperair on 2008-02-05
I reckon refresh rates only really matter much when you're staring at a CRT monitor. They flicker like hell at lower refresh rates. LCDs don't have the effect, much.

---

### Post by tw.bodean on 2008-02-05
I've just recently started my delve into Ubuntu.  After I had initially setup the OS, I tinkered around with it for about an hour or two.  Later, when I was looking for where I could change the screen resolution and found the option in **System\Preferences\Screen Resolution** amazingly enough.  I noticed that my monitor was at the correct resolution (1680x1050) but was also set at ~50hz.  Clicking on the drop down menu resulted in only that single 50hz option.  I continued to look for a way to change this and found that, I too, had my monitor set to 'Generic LCD Display'.  Changing that to my current monitor (Samsung SyncyMaster 226BW (digital)) resulted in a much more acceptable 62hz.

Perhaps try setting your display to something else?

---

### Post by daverich on 2008-02-05
> **hyperair said:**
> I reckon refresh rates only really matter much when you're staring at a CRT monitor. They flicker like hell at lower refresh rates. LCDs don't have the effect, much.

LCDs dont have the affect at all.

it's a static picture.

- Edit - to add to this this is why CRTs look flickery on film but lcds look fine - there's no refreshing going on at all with the lcd, the pixels are either on or off as it were, not constantly refreshing like a CRT.

Kind regards

Dave Rich

---

### Post by legend2440 on 2008-02-05
I found this xorg.conf for the t42. The only difference I see is your Defaultdepth is 16 and theirs is 24
Anyway, if you want to you can try theirs but first make a backup of yours

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak   

Here is url for alternate xorg.conf

[http://mergy.org/2008/01/27/ubuntu-gutsy-and-ibm-thinkpad-t42-xorg-configuration/](http://mergy.org/2008/01/27/ubuntu-gutsy-and-ibm-thinkpad-t42-xorg-configuration/)

---

### Post by lnlds on 2008-02-05
i changed my default depth to 16 so i could run compiz at my native resolution since my video card only has 32mbof ram. I guess perhaps my eyes just might be tired from some late nights then? It must be my imagination or something then.

---

### Post by hyperair on 2008-02-05
Probably late nights. I get the eye fatigue thing from time to time too. Burns like hell. Also you might like to try lowering the brightness of your LCD backlight. I can't, but if you can it's better. Sometimes I feel my monitor's a tad too bright, so I've switched to using dark themes.

---

### Post by LowSky on 2008-02-05
switch to a  darker theme, lower the LCD's brightness, sit further away, dont sit in the dark alway have lights on in the room, go to bed early, eat your carrots, dont look at the sun, dont poke your eyes... doing a few of these might help your eyes..

enjoy

;)

---

### Post by hyperair on 2008-02-05
> **LowSky said:**
> ...dont poke your eyes...

Good lord, who in the world does that?!

---

### Post by erginemr on 2008-02-05
Your xorg.conf file starts OK, but goes awry as a complete mess after this line:
```
...................
...................
# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
Inputdevice "Synaptics Touchpad"
EndSection
Section "Module"
Load "glx"
Load "GLcore"
Load "v4l"
EndSection
Section "device" #
Identifier "device1"
Boardname "ati"
Busid "PCI:1:0:0"
Driver "ati"
Screen 1
Option "MergedFB" "off"
EndSection
Section "screen" #
Identifier "screen1"
Device "device1"
Defaultdepth 16
Monitor "monitor1"
SubSection "Display"
Depth 16
Modes "640x480@60"
EndSubSection
EndSection
Section "monitor" #
Identifier "monitor1"
Vendorname "Plug 'n' Play"
Modelname "Plug 'n' Play"
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
Gamma 1.0
EndSection
Section "ServerFlags"
EndSection
```

I suggest you to back up your current config file and reconfigure your X server with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by parts-man73 on 2008-02-05
I noticed that when I upgraded from feisty ---> gutsy, it changed my screen resolution and it seems that the refresh rate might of changed at the same time. It now hurts my eyes too! 

On my laptop...no problems, for the reasons stated earlier in this thread. but on my desktop computer with a CRT monitor, I get a headache almost immediately.

Brian

---

### Post by Jerry N on 2008-02-05
Ubuntu and LinuxMint both report 50hz refresh for my Samsung LCD display.  However, when I check the menu on the Samsung, it says it is working at 60.  I quit worrying about it.

Jerry

---

### Post by hyperair on 2008-02-05
It's all in the mind!! =D Anyway it reports 50Hz for me too on my desktop, but my monitor shows 75Hz.

---

