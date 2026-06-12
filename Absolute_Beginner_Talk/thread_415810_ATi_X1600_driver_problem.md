---
title: "ATi X1600 driver problem"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by cubbs80 on 2007-04-20
Hey all,

I followed the ATi driver install instructions found in the sticky above, as well as the instructions I found on the following page (different clean installs of feisty):

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

My problem is that once the splash screen competes, I'm greeted with a blank screen.  It's as if the driver has defaulted to a resolution or refresh rate that my monitors are incapable of displaying.  Both my main LCD and the secondary CRT I connected for testing are getting signals from the video card but I have no display.  Reverting to the xorg.conf backup I made before installing the drivers brings me back to a usable desktop.

Something I'm doing wrong?

Cheers,
cubbs80

---

### Post by cubbs80 on 2007-04-20
No input at all?

bump bump

---

### Post by Maglio on 2007-04-20
i'm having the same issue.  i have an x800 xl, and i tried to use envy on a fresh install of 7.04.  the first xorg file is the default used by ubuntu when i first loaded it up.  the second is the xorg after i installed the ati drivers through envy.  when i reboot, i get a blank screen after the ubuntu logo with the orange loading bar.  i've tried like 5 or 6 different guides on how to install the drivers, but all of them come up with a blank screen when i reboot.  i am going to post the entire file, because i am very, very new to ubuntu and linux in general and don't know what is needed

xorg - default
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Driver		"ati"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Disable"
EndSection


XORG.CONF - blank screen on reboot
Section "ServerLayout"
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
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Driver      "ati"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
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

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

---

### Post by Maglio on 2007-04-20
so no one is able to help with this?

it's getting kind of frustrating to not have a screen size higher than 1024x768.  eveything is too big.  could someone please help with this issue?  i can't be the only one having the issue.

i have searched around the web for a solution, but have been unable to come up with anything.  please, please, please help.

please.  (one more for good measure)

---

### Post by pupdawg on 2007-04-20
Yes I have a X1600 Pro and have been using Ubuntu for a long time but in Feisty I also boot to the black screen... I have a feeling this is an ATI problem and we will be stuct for awhile... the guides are all good but for some of us this issue happens. :(

---

### Post by igknighted on 2007-04-20
```
Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
[B]Depth 24
Modes "1024x768" "800x600" "640x480"[/B]
EndSubSection
EndSection
```

Add the resolution you desire to this section (the one near the very end of the file) in the format of the others (first in the line).  Since you are using 24 as the default color depth, you only need to add it to that line which I bolded.  Then restart X (ctrl-alt-backspc) and you should be good.

---

### Post by igknighted on 2007-04-20
nm... wrong section... you seem to have used ati-config which leads to a messy xorg.conf... do you have the ati firegl control center installed?  Try using that to change the resolution

---

### Post by kc0eks on 2007-04-20
i also have this card but have not yet upgraded, this worries me a bit :/

I had numerous problems getting this card to work right, however the fglrx driver seems to work somewhat well.

I hope this problem is resolved, or somewhat unique to the few who have posted...

---

### Post by traffas on 2007-04-24
I have not been able to get the x1600 to work with fglrx and 64 bit Feisty. It worked like a dream under Edgy i386. Does anyone know how to beat the black screen on reboot?

---

