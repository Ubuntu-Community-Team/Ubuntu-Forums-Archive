---
title: "Damn resolution and refresh rate!!"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by sethfc on 2007-12-21
Hey Guys,

So my resolution/refresh rate was somewhat of a problem.  i edited xorg.conf to get a decent 1152x768 @ 72.

When i was messing with the login screen, suddenly everything got screwed up.

Now, my resolution says 1152x768, and has a crappy 50 refresh rate.  But here's the crazy part: it doesnt fit the screen.... as in, i move my mouse all the way to the right, and the screen continues.  It's hard to explain, but fixing the ''zoom'' using my monitor buttons does nothing.  its like i can slide the screen around by pushing my mouse to the far edges of the screen.

here's my xorg.conf:

```
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
	Identifier	"Generic Video Card"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"E70fb-5"
	Vendorname	"ViewSonic"
	Modelname	"ViewSonic E70f-5/E70fb-5"
	Horizsync	30-70
	Vertrefresh	50-160
  modeline "1152x864" 107.48  1152 1208 1336 1584   864  864  867  904 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"E70fb-5"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1152	864
		Modes		"1152x864@75"	"1280x960@60"	"1024x768@43"	"1280x1024@60"	"1024x768@60"	"1400x1050@60"	"1024x768@70"	"1024x768@75"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
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
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" #    
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" #    
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"	"640x480@72"	"640x480@75"	"640x480@85"	"800x600@56"	"800x600@72"	"800x600@75"	"800x600@85"	"800x600@60"	"832x624@75"	"1024x768@85"	"1024x768@75"	"1024x768@70"	"1024x768@60"	"1024x768@43"	"1152x864@75"	"1280x960@60"	"1280x1024@60"	"1400x1050@60"
	EndSubSection
EndSection
Section "monitor" #    
	Identifier	"monitor1"
	Vendorname	"ViewSonic"
	Modelname	"ViewSonic E70f-5/E70fb-5"
	Horizsync	30-72
	Vertrefresh	50-160
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

My monitor is a Viewsonic E70FB.  It CAN do 1152x864 @ 75 herts, as it does in windows.

my graphics cards is a 7800GT 256MB pci express.

Ubuntu 7.10 64-bit

thanks,
seth

---

### Post by shadow-of-sin on 2007-12-21
Try reconfiguring xorg to get it back to normal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by The Tronyx on 2007-12-21
If shadow-of-sin's suggestions don't work, you might want to change the horizontal and vertical sync values in xorg.  I just pulled up the specs on your monitor:

> 
Max Sync Rate (V x H)  	 160 Hz x 70 KHz

From [http://shopper.cnet.com/crt-monitors/viewsonic-e70fb-display-crt/4014-3175_9-32177281.html?info=user&#p5](http://shopper.cnet.com/crt-monitors/viewsonic-e70fb-display-crt/4014-3175_9-32177281.html?info=user&#p5)

---

### Post by CatKiller on 2007-12-21
I very much doubt that you have a 50 Hz refresh rate. Compiz incorrectly reports the refresh rate, and it often gets displayed in the low 50s even when it isn't.

It's also possible that you've inadvertently zoomed in with the Compiz plugin. Try pressing your Windows key and scrolling down with your mouse wheel.

---

### Post by sethfc on 2007-12-21
i tried reconfiguring the xorg, and now i see my login box, but its totally blurry and what not, and i cant do anything.

before that i tried inputting the max refresh rates for horizontal and vertical.  no luck either

-_-

anyone have an E70FB viewsonic and a 7 series Nvidia card I can copy their xorg.conf?

---

### Post by sethfc on 2007-12-22
big bump

---

### Post by Bachstelze on 2007-12-22
Get a clean xorg.conf back as shadow-of-sin told you, and then paste it so we can tell you what you need to edit.

---

### Post by sethfc on 2007-12-22
OK, I reformatted.
Did updates.
Installed the Nvidia-glx-new
Made the visual affects under System > Appearance "Normal"
Currently 1280x1024 @ 50 Hz (no emerald installed).

here is my xorg.conf

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"E70fb-5"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"E70fb-5"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

Monitor is a Viewsonic E70FB (it CAN do 1152x864 @ 75 in windows)
Card is a 7800GT 256 PCI-E.

thanks guys,
seth

---

### Post by sethfc on 2007-12-22
bump for a clean xorg.conf that people can tell me what to do with =p

---

### Post by sethfc on 2007-12-23
after work bump

---

### Post by Bachstelze on 2007-12-23
```
	SubSection "Display"
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
```

change to :

```
	SubSection "Display"
		Depth		24
		Modes		"1152x768_72"
	EndSubSection
```

Also, you will need to fill in your monitor's refresh rates, like this :

```
Section "Monitor"
	Identifier	"E70fb-5"
	HorizSync	30.0 - 80.0
	VertRefresh	50.0 - 75.0
	Option		"DPMS"
EndSection
```

However, **do not** just copy and paste those values, but look for the correct ones in your monitor's manual. **Incorrect values might, and most likely *will*, damage your monitor, especially if it's a CRT.**

---

### Post by sethfc on 2007-12-23
i did your changes, and now i am stuck at a max of 1080x768 @ 50.  Here is the xorg...

```

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
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"E70fb-5"
	HorizSync	30-70
	VertRefresh	50-160
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"E70fb-5"
	Defaultdepth	24
	SubSection "Display"
		Depth		24
		Modes		"1152x768@75"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

i'd go and change stuff as I thought would be good but i've had WAY too many problems, so i'm giving it a rest so i dont hurt something =x

---

### Post by sethfc on 2007-12-24
*sigh* bump

---

### Post by sethfc on 2007-12-24
if i dont include the "Virtual" bit under the screen section, i can never get into 1152 x 864.

Adding that allows me to get that resolution.  BUT it seems like I'm zoomed in again... so i tried the window key + scrolling and I am zoomed out all the way.

wtf.

---

