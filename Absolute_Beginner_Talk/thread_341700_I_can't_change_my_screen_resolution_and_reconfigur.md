---
title: "I can't change my screen resolution and reconfiguration doesn't work"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by adrock on 2007-01-19
Hi first off all i apologize because my english is not very good
Im new using ubuntu, last week i install ubuntu 6.10 and the only resolution i can use is 640x400 i have an ati radeon all in wonder 7500 wich i can't use, when i tried to install ubuntu whit that card the installation fails anyway my motherboard have integrated video in this very moment i dont have the name of the card but it's a intel and the correct driver for this one is i810, i have an hp mx70 monitor i all ready run the  dpkg-reconfigure xserver-xorg and change the xorg configuration whit the right parameters of my monitor and i still can't use any other resolution in the xorg configuration archive appear another 3 resolutions but when i try to change the resolution the list box only displays one, please help me i really want to use ubuntu as my primary os.

i post my xorg.conf file

Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
FontPath "/usr/share/fonts/X11/misc"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "latam"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
Driver "i810"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "MX70"
Option "DPMS"
HorizSync 30-70
VertRefresh 50-120
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
Monitor "MX70"
DefaultDepth 16
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
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection


This one have all the default values except for HorizSync VertRefresh those where different but i change it for the values of my monitor.
Thanks

---

### Post by azkehmm on 2007-01-19
First. Your english isn't that bad. take a look at the World of Warcrack forums, and you'll be surprised how bad english, even native english speakers speak/write.

 Second, I'm no guru or anything, but I have an idea that might work.

 Third, what kind of errors do you get when you try to install ubuntu with your ATI card in the machine? Is it the installation itself that fails, or is it when you try to boot up Ubuntu after installation?

 If it's the latter, you could try to install the Xorg ATI drivers from recovery mode, ie. without firing up Xserver. Use "sudo aptitude" and find the drivers, after enabling the extra repositories. 

 If it's the first, you could try and flip your ATI into the machine after installing ubuntu, and then try and install the drivers from aptitude, and edit xorg.conf.

 That was a couple of ideas, at least, but like I said, I'm no guru :)

---

### Post by alienexplorers on 2007-01-25
Try running the gtf Modeline creator.  It creates modeline statements that get added to your xorg.conf file in the monitor section.  This allows you to set resolution and refresh rates for ubuntu.

I have listed here my xorg.conf for reference:

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 7200 (R100 QD)"
	Driver		"ati"
	BusID		"PCI:0:9:0"
	VideoRam	32000
EndSection

Section "Monitor"
	Identifier	"Delta DE-570 BA"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	60-85
	Modeline "1024x768_85.00"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync
	Modeline "1280x768_85.00"  118.53  1280 1368 1504 1728  768 769 772 807  -HSync +Vsync
	Modeline "1280x960_70.00"  120.84  1280 1368 1504 1728  960 961 964 999  -HSync +Vsync
	Modeline "1280x1024@75i" 64.12 1280 1312 1552 1584 1024 1046 1054 1077 interlace
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 7200 (R100 QD)"
	Monitor		"Delta DE-570 BA"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1280x768" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

