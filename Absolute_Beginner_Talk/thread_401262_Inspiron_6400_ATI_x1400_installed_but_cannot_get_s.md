---
title: "Inspiron 6400 ATI x1400 installed but cannot get screen resolution"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by englishaugust on 2007-04-04
Hi to the helpful gurus out there :)

I installed ubuntu edgy on an inspiron 6400 with ATI x1400 256 MB mobility radeon. I was able to  install the drivers for the video card using [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2)

But, my maximum screen resolution is 1024x768.

I have already done sudo aticonfig --initial but that does not seem to have done it.

I also looked in the ATI catalyst control center in the menu and even that has 1024x768 as the maximum resolution.

Would really appreciate if someone could help :) It took me about a week to get the wireless working (Broadcom 1390) and I will not give up on Ubuntu, no matter what, am never going back to windows again.

Thanks

---

### Post by Kobalt on 2007-04-04
Open a Terminal and type this :
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select the resolutions you want as available by hitting the space bar, then press Enter. 
Finally, restart X with Ctrl+Alt+Backspace.

---

### Post by englishaugust on 2007-04-04
Thanks for replying. I tried doing what you suggested. The first screen is asking for driver, the default  highlighted is vesa, then it asks for resolutions, i chose 1280x1024 and restarted X. Still nothing, I am limited to 1024x780. Another problem has now appeared, my scrolling in firefox is horrible. 

Am posting my xorg.conf file below, please see if this helps:

Section "ServerLayout"
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

Section "ServerFlags"
	Option	    "AIGLX" "off"
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
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
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

---

### Post by Kobalt on 2007-04-05
As you installed the drivers for your ATI card you should have selected them instead of VESA, this is why your scrolling is a pain... You should enter the command again and select FGLRX instead of VESA.

PS: make sure you so select the resolutions you want as available by **hitting the space bar**.

---

### Post by englishaugust on 2007-04-05
Kobalt, you absolutely rock :) Did exactly as you said this time and everything works. Thanks so much. I must have messed up in choosing vesa by mistake last time.

By the way, how does one make that box within a reply in this forum where people usually put the code?

Thanks once again :)

---

### Post by technodigifreak on 2007-04-16
This worked for me on a Lenovo Thinkpad z61m w/ ATI Radeon Mobility X1400 running Feisty Beta

Thanks for the help.

PS.  Beryl seems to be a wash on the z61m for the time being.

---

### Post by chemisus on 2007-04-20
worked for me on dell e1505 x1400 feisty, after doing the accelerated device installation. thanks.

---

### Post by cheesewhiz on 2007-04-20
would this work for an nvidia card??

---

### Post by cheesewhiz on 2007-04-21
No response, eh?

---

