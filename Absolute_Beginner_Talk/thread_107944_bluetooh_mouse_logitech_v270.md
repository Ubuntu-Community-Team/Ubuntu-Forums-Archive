---
title: "bluetooh mouse logitech v270"
date: 2005-12-24
forum: Absolute Beginner Talk
---

### Post by bflores on 2005-12-24
Help i have followed everything i can find on added a blue tooth mouse.  It looks like it is connected but it is note moving.  i am wondering what i did wrong here is my hcitool output:
root@crc-bfloreslt:/home/bflores# hcitool con
Connections:
        < ACL 00:07:61:3B:9C:6B handle 41 state 1 lm MASTER
root@crc-bfloreslt:/home/bflores# hcitool info
root@crc-bfloreslt:/home/bflores# hcitool info 00:07:61:3B:9C:6B
Requesting information ...
        BD Address:  00:07:61:3B:9C:6B
        Device Name: Bluetooth Travel Mouse
        LMP Version: 1.2 (0x2) LMP Subversion: 0x545
        Manufacturer: Cambridge Silicon Radio (10)
        Features: 0xfc 0xff 0x0f 0x00 0x08 0x08 0x00 0x00
                <encryption> <slot offset> <timing accuracy> <role switch>
                <hold mode> <sniff mode> <park state> <RSSI> <channel quality>
                <SCO link> <HV2 packets> <HV3 packets> <u-law log> <A-law log>
                <CVSD> <paging scheme> <power control> <transparent SCO>
                <AFH cap. slave> <AFH cap. master>

and here is my : xorg config 

Section "Module"
	Load	"GLcore"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Identifier	"Bluetooth Mouse"
	Driver		"mouse"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
	Option		"Buttons"		"5"
	Option		"Name"			"AutoDetected"
	Option		"Vendor"		"AutoDetected"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
        InputDevice     "Bluetooth Mouse"



Help i am so lost

---

### Post by tsiMental on 2006-08-30
[Follow these instructions and you should make it work.]("http://www.ubuntuforums.org/showthread.php?p=1440347#post1440347")

Regards,
Håvar

---

### Post by steeef on 2007-12-11
I have this exact same mouse with the exact same problem. Everything I read said that Gutsy should have no issues detecting it, but I couldn't get to the point where I could use it. After following the linked instructions (and running "hidd --search" until the mouse was finally found), it works flawlessly. Thanks!

---

### Post by milanmm on 2008-01-04
Is it working with the wheel scrolling after the reboot? Some people have an issue with that, see [http://ubuntuforums.org/showthread.php?t=404112]("http://ubuntuforums.org/showthread.php?t=404112"). I would like to know whether for somebody it is running without a problem.

---

### Post by jetpeach on 2008-01-16
darn, i was _just_ about to buy this mouse for my ubuntu laptop. any luck getting it to work? now i guess i'll have to hold off

---

### Post by milanmm on 2008-01-18
I love the mouse, it was very simple to set it up, the only problem is the wheel scrolling not working automatically. There has to be a trick how to fix it as it work after you follow the procedure mentioned in  [http://ubuntuforums.org/showthread.php?t=404112]("http://ubuntuforums.org/showthread.php?t=404112"), but has to be done after each reboot :-(.

---

