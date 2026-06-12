---
title: "Can't get OpenGL to work with ATI card"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Aelwynn on 2007-04-01
Yesterday I decided to install Ubuntu Edgy 6.1 and Wine onto one of my PC's. Even tho I'm brand new to Linux systems, things went fairly smoothly with one exception. 

I can't get my ATI Raedon 9600XT card to run OpenGL. When I run $ glxinfo | grep "direct rendering" in Terminal I get the following Error:

> Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No


And here is my xorg.conf

> Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "on"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480" "256x256"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480" "256x256"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480" "256x256"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480" "256x256"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480" "256x256"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480" "256x256"
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

Section "DRI"
	Mode         0666
EndSection

Any help would be greatly appreciated.

---

### Post by Campingman on 2007-04-01
Here are a couple of guide that should help you out

For fglrx driver
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

Radeon open source driver
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

One of these drivers should suit your card

---

### Post by jvc26 on 2007-04-01
First of all:
```

Section "Device"
Identifier "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
Driver "ati"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "on"
EndSection

```
Looks wrong - this suggests that you have 2 devices, one the computer recognises as the device (The ATI Technologies, Inc. RV350 AR [Radeon 9600 XT] device) and one that you have added - below that section.

When you look at the screen section:
```

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
Monitor "Generic Monitor"
DefaultDepth 24

```
It is referencing the device ATI Technologies, Inc. RV350 AR [Radeon 9600 XT] not the line that it looks like you have added in.

I would suggest that you take a peek on here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
Which is what I used to get my ATI set up. 

I think what you were probably trying to get set up was something like this below (I'm not sure whether this will or won't work though, as although I have spent a fair bit of time playing with xorg.conf I am not 100% sure of its inner workings) presuming you added in the lines yourself:

Rather than:
```

Section "Device"
Identifier "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
Driver "ati"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "on"
EndSection

```
Were you actually aiming for something like this?:
```

Section "Device"
Identifier "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "on"
BusID "PCI:1:0:0"
EndSection

```
I.e. only one device section, but editing the one that was actually there (which is what I've had to do to get mine working)

My advice would be to take a look at the above link, and also if it tells you later that your xorg.conf doesnt work and that it will only boot to a terminal window, you can reconfigure your xorg.conf:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
Which for me has allowed me to reboot back into my Xserver and try again.
I hope some of this massive post helps :) ATIs can be a bit of a pain to get working
Il

---

