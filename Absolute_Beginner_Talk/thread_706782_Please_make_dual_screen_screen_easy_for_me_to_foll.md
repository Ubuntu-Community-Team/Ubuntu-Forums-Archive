---
title: "Please make dual screen screen easy for me to follow"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Lderan on 2008-02-24
I have a 2nd monitor plugged into my radeon 9250 graphics card and for the life of me I can't get it to work, I messed with the xorg.conf, only to mess everything up. 

Is there an easy guide out there to follow for dual screening? I haven't yet dual screened before.

---

### Post by timbounceback on 2008-02-24
System->Administration->Screens and Graphics

---

### Post by Lderan on 2008-02-24
Only my main screen appears in that menu, the 2nd screen shows the boot up till the login screen.

---

### Post by Lderan on 2008-02-25
Very sorry for the double post, but is there no easy way of setting it up, I have followed a few guides and all to no avail. Helps please

---

### Post by markbusu on 2008-02-25
Do you have a Graphics card with 2 outputs..(15pin/Digital) ? or are you using an Onboard Card with the radeon 9250 GFX Card?

---

### Post by Lderan on 2008-02-25
The card does have 2 outputs, dvi and vga ports.
I have installed the ATI drivers but for some strange reason it has really messed up my screen on my main monitor, tho it is now displaying the same screen on both monitors.

I have no idea what is going on, I have attached the xorg.conf file
It seems to happen when I type "sudo aticonfig --initial" and reboot

---

### Post by Crooksey on 2008-02-25
I have tweaked your xorg.conf, try using the one below:

```

Section "ServerLayout"


	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "GLcore"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "DELL E196FP"
	VendorName   "Dell"
	ModelName    "Dell E196FP"
	HorizSync    31.0 - 83.0
	VertRefresh  56.0 - 76.0
	Gamma        1
	ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	ModeLine     "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
	ModeLine     "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
	ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine     "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	ModeLine     "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
	ModeLine     "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	ModeLine     "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	ModeLine     "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
	ModeLine     "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	ModeLine     "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
	ModeLine     "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	ModeLine     "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
	ModeLine     "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	ModeLine     "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Driver      "ati"
	BoardName   "ati"
	Option	    "MergedFB" "off"
	Option	    "DesktopSetup" "horizontal"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BoardName   "ati"
	Option	    "MergedFB" "off"
	Option	    "DesktopSetup" "horizontal"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Monitor    "DELL E196FP"
	DefaultDepth     24
	SubSection "Display"
		Virtual   1792 1344
		Depth     24
		Modes    "1280x960@60" "1280x1024@60" "1280x1024@75" "1280x960@75" "1152x864@75" "1400x1050@60" "1024x768@60" "1400x1050@75" "1024x768@70" "1600x1200@65" "1024x768@75" "1600x1200@60" "832x624@75" "1792x1344@60" "800x600@60" "800x600@75" "800x600@72" "800x600@56" "640x480@75" "640x480@72" "640x480@60"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by Lderan on 2008-02-25
It still loads into low graphics mode, I checked under "System->Administration->Screens and Graphics"
And it says its using the driver "vese", that is not right is it?

---

### Post by Crooksey on 2008-02-25
No, try using my xorg.conf

---

### Post by Lderan on 2008-02-25
It works now, i somehow missed installing one of the packages.

Thank you very much, but alas in the admin screens and graphics thing my 2nd monitor is still not showing up.

---

### Post by Lderan on 2008-02-25
Following guides and stuff this is what my current xorf.conf looks like, Yet it doesn't work.
helps please :confused:

```
Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Screen         "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "EnableMonitor" "crt1,crt2"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

---

### Post by Lderan on 2008-02-25
this is not a bump at all!

I think the problem is that I am not telling it which port on my graphics cards is screen 1 and which is screen 0

---

### Post by Crooksey on 2008-02-26
If both monitors are not running at the same resolution, then bit of the screen will be cut off.

---

### Post by Lderan on 2008-02-26
Ah okays, but alas it still doesn't work. This is rather strange.
I have tried using the MergedFB method but the 2nd monitor just turns into a over bright clone for some unknown reason.:confused:

---

