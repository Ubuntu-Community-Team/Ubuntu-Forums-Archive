---
title: "Problem when I upgraded to Feisty"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by lazyrussian on 2007-04-12
I'm having an interesting problem.

I update Kubuntu Edgy to feisty using the ugrader tool. When it restrted my computer, it brough up the login screen as if I were in terminal (looks like MS-DOS). After I put in my login information I'm still at the command line. 

How do i enable the GUI/KDE environment to startup when I start my computer....what happened in the first place?

I can't really do anythign if my computer is in terminal/konsole/command line mode...


(I'm on my roomates computer typing this now)

---

### Post by lazyrussian on 2007-04-12
Oh yeah, startx doesn't work

---

### Post by bwhite82 on 2007-04-12
I would try reinstalling kdm

> sudo apt-get remove kdm
sudo apt-get install kdm

It should automatically set it up so that it boots straight to kdm instead of the console. If it still boots to the console afterwards then it is probably a video/driver problem. One way to check is to simply type in the command line:

> startx

If problems were encountered, then X will tell you on screen what caused it.



Cheers

---

### Post by zvacet on 2007-04-12
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

### Post by bwhite82 on 2007-04-12
> **lazyrussian said:**
> Oh yeah, startx doesn't work

Hopefully it's not the dreaded "No screens found" error message. (Which in fact has absolutely ziltch to do with the fact that X is or is not detecting your screen or if your screen is or is not set up properly in your xorg.conf)

---

### Post by macogw on 2007-04-12
X is working on his comp now.  He brought it over my dorm :p Since I'm not an ATi user, though, I have no idea how to fix this new problem.  Trying to use fglrx/xgl, the image is completely distorted and squiggly.  fglrxinfo says:
Xlib: extension "XFree86-DRI" missing on display ":0.0".
and then makes a bunch of references to mesa instead of to ati.  How do we fix that?

---

### Post by bwhite82 on 2007-04-12
I just spent the last 2 days with this exact same problem it was a pain, I finally had to revert back to the older kernel 2.6.17

First, make sure the kernel is loading your hardware drivers. (As it's booting  up, switch to 'verbose mode' ALT+F1 and look for errors)

While I cannot give comprehensive instructions on how to fix the issue, here are some things that may help:

Add this line to the bottom of your /etc/modprobe.d/blacklist (Per ATI's instruction)
> 
# causes fglrx to fail and mesa drivers to load
blacklist agpgart

I will post my xorg.conf as an example even though his may vary:

> Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
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
	Load  "vbe"
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
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
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

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
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

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

I am currently using ATI's latest driver, 8.35.5. Hope this helps in any way.

Also, It's always a good idea when installing a new driver to:
> 
sudo depmod

Cheers

---

### Post by lazyrussian on 2007-04-12
Thanks. I don't know if I'll go back to the old kernel....beryl is not a must for me. As Macogw said above, I can log back in into the graphical version/gui of kdm. 

I'll work on fixing the fglrx driver or wait till it's fixed.

Thanks for the suggestions and help! (everyone who posted)

---

