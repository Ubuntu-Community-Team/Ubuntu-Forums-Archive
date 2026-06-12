---
title: "Restricted Drivers"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Fuzzgun on 2007-04-21
AMD Opteron 180
Radeon X1950 Pro AGP 512MB user.

Just reinstalled Ubuntu and have updated to Ubuntu 7.04 (Feisty Fawn).
I haven't tried installing any ATI graphics drivers yet as the system seems to be working fine with the default drivers but I have noticed in the desktop panel the following program - System/Administration/Restricted Drivers Manager. 
When I open this program 'ATI accelerated graphics driver' is listed, the 'Enabled' box is not checked and the 'Status' is listed as 'Not in use'.

Does anyone know if the Enabled box should be checked?

---

### Post by mikewhatever on 2007-04-21
As you may know, Ubuntu is based on the philosophy of open/free software including drivers. ATI drivers are closed source, so they are not enabled and where not included up until 7.04. If you want to use that driver and not the native Ubuntu one, do enable it. You can check if you have direct video rendering with the current driver
> glxinfo | grep rendering
If the answer is 'Yes', then I don't see the reason to change it. If not, which probably is the case, and you want direct rendering, ATI restricted is the way to go.

---

### Post by matthew on 2007-04-21
If you check the "enabled" box, it will download, install, and configure the ATI driver for you. I just did it and it was quick and painless.

---

### Post by Fuzzgun on 2007-04-21
Just updated the ATI driver using [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide).
After rebooting, Ubuntu loads fine and everything seems OK. The ATI 'Enabled' box in the Restricted Drivers Manager section is now checked but the Status is 'Not in use'.

This is the output of fglrxinfo:

fuzzgun@fuzzgun-desktop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)


here's my xorg.conf

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
	Option		"XkbLayout"	"gb"
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
	Identifier	"ATI Technologies, Inc. ATI Default Card"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"PLE431"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. ATI Default Card"
	Monitor		"PLE431"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

Section "Extensions"
        Option  "Composite" "Disable" 
EndSection


Anyone got any ideas?

---

### Post by koztaz on 2007-04-21
Same here... But as I read forums there are a lot of ppl complaining the same problem :(

---

### Post by Dexter. on 2007-04-22
Try running this script called Envy, [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

