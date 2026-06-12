---
title: "bluetooth logitech mx1000 mouse problem"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by stonefeet on 2006-07-05
i've read all over these forums for a solution and nothing i tried would work
the side buttons aren't a huge deal, but the scroll whell randonly stopped working so i've been on the hunt to fix it once and for all

here's my cat /proc/bus/input/devices
```
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c70e Version=4001
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:1d.7-3.3.2/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c70a Version=4001
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:1d.7-3.3.3/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd mouse0 event3 ts0
B: EV=f
B: KEY=c0002 400 0 0 fff0001 f80 78000 6039fa d841d7ad 9e0000 0 0 0
B: REL=1c3
B: ABS=1 0

I: Bus=0003 Vendor=0a5c Product=3502 Version=0100
N: Name="HID 0a5c:3502"
P: Phys=usb-0000:00:1d.7-3.4.2/input0
S: Sysfs=/class/input/input4
H: Handlers=kbd event4
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
B: LED=7

I: Bus=0003 Vendor=0a5c Product=3503 Version=0100
N: Name="HID 0a5c:3503"
P: Phys=usb-0000:00:1d.7-3.4.3/input0
S: Sysfs=/class/input/input5
H: Handlers=mouse1 event5 ts1
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

```

and my xorg.conf

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL 2005FPW"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Monitor		"DELL 2005FPW"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
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

```

any help is much appreciated

---

### Post by wh0rd on 2006-12-15
So you've got the MX1000 mouse and MX5000 Keyboard with the USB dongle.
Well I'm in the same situation. What seems to work is to unplug the USB dongle and repluging it back in at login screen.

---

### Post by Kenja on 2006-12-18
From what I have gathered, the problem is in the Logitech reciever.  I'd look into getting the keyboard and mouse functional without using the Logitech receiver/charger as the bluetooth transceiver.

---

### Post by wh0rd on 2007-02-14
Actually it worked fine under SUSE.

---

