---
title: "Problems with monitor setting"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by Camellia on 2006-07-22
Hi everyone I'm currently using a Laptop with a extra independent display connected to it (I do it because the screen of my laptop is way too small).

When I was using WinXP I used the External Extra display as the main monitor and the laptop one as an extended so I could drag one window from one display to another.

The problem is, when I finally come to Linux (Just a few days ago) I'm not able to find the monitor setting. As a result my two displays show exactly the same thing. What's weird is when I trying to play a movie the display of the laptop will show the picture but not the external one, it will show the frame of the player and leave the content black (Um...which is as big as the picture). 

Can anyone be so nice to tell me how to go to monitor setting (not the resolution one), or simply how to turn my laptop screen off so the External one will show the picture nicely as a result?

Thank you for reading my humble question.

---

### Post by Ziox on 2006-07-22
perhaps this command may help, but i'm not expert at linux:

sudo dpkg-reconfigure -xserver-xorg

---

### Post by Camellia on 2006-07-22
Thank you so much for the inputing:)

Forgive me but what exactly that line of command will do?

---

### Post by Ziox on 2006-07-22
it reconfigures xorg.conf, which handles all of inputs and outputs, such as mouse, keyboard, graphics card and of course monitors.

---

### Post by zxee on 2006-07-22
You can try what Ziox recommended but I'm not sure it will help. Is there a way to get dual head support though dpkg-reconfigure...?
Anyway dual head is what you're looking for you can do some searching on that phrase there is a recent thread here: [http://www.ubuntuforums.org/showthread.php?t=189977&highlight=dual+head](http://www.ubuntuforums.org/showthread.php?t=189977&highlight=dual+head)
although that thread is also bringing up another feature (xgl) Search for dual head + linux and dual head ubuntu. Good luck and let the forum know how you make out. Your experiances can help others plus the more you try the more ideas others will put forward.

Added: Also look at twinview there's a recent thread here: [http://www.ubuntuforums.org/showthread.php?t=85769&highlight=dual+head+laptop](http://www.ubuntuforums.org/showthread.php?t=85769&highlight=dual+head+laptop)

---

### Post by Ziox on 2006-07-22
Yeah...like my signature states, i'm just a noob.  But i'm just trying to help out as much as i can...sorry for the ignorance....

---

### Post by Camellia on 2006-07-22
Thank both of you very much^^

zxee: I'll try them out, that seems gonna take me a whole night:)

Ziox: NO, you ain't a noob at all, I am. I'll definitely try that command.

---

### Post by Ziox on 2006-07-22
Silly me, i have the "Ubunt Hack" with me right now, and in it, it details how to have dual monitor support, so if you can't get it to work with threads provided by zxee, then I will write out the steps if you want.

---

### Post by zxee on 2006-07-22
Ziox, What is the "Ubuntu Hack"? If it's a book that available perhaps you could provide the publisher. I sometimes refer to Knoppix Hacks an O'Reily book which has many good troubleshooting guides.

---

### Post by Ziox on 2006-07-22
yeah..Ubuntu Hacks is also published by O'Reily

---

### Post by zxee on 2006-07-22
Thanks Ziox, I'll have to check it out.

---

### Post by Camellia on 2006-07-22
Ok everyone Ziox has solved this issue nicely. And yes here I'll post what Ziox told me to do.

If you want an extended display then keep reading

First backup the xorg.conf file which is located at /etc/X11/
and then open the original one and modify it as following:

-------------------------------------
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"1 ATI Technologies, Inc. M9+ 5C61 [Radeon Mobility 9000 (AGP)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
Screen	0
EndSection

Section "Device"
	Identifier	"2 ATI Technologies, Inc. M9+ 5C61 [Radeon Mobility 9000 (AGP)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
Screen	1
EndSection

Section "Monitor"
	Identifier	"1 Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"2 Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"1 Default Screen"
	Device		"1 ATI Technologies, Inc. M9+ 5C61 [Radeon Mobility 9000 (AGP)]"
	Monitor		"1 Generic Monitor"
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

Section "Screen"
	Identifier	"2 Default Screen"
	Device		"2 ATI Technologies, Inc. M9+ 5C61 [Radeon Mobility 9000 (AGP)]"
	Monitor		"2 Generic Monitor"
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
	Screen		"1 Default Screen"
        Screen	"2 Default Screen" LeftOf "1 Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerFlags"
	Option "Xinerama"	"true"
EndSection

Section "DRI"
	Mode	0666
EndSection
----------------------------------------------------

When it is done, save the file and our work and restart X by pressing ctr+alt+backspace.

As a result you would have an extended display^^

BTW: you may change some part of the text such the identifier of the device and so on.

---

