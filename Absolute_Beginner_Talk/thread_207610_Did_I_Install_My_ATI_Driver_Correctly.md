---
title: "Did I Install My ATI Driver Correctly?"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by TorxT3D on 2006-07-02
I want to be able to use that 3d desktop XGL with my radeon 9800 pro

I downloaded the "ati-driver-installer-8.26.18-x86.run" from ati's website and used the sudo command to run it and installed it.  I chose to install normal, nothing customized.

I "fglrxinfo" and its coming up with Mesa information.  From what ive read, it should say "ATI Fglrx" in order to be able to use XGL.  I edited the xorg.conf file to say fglrx instead of ati like everyone said, but the only new difference is the ATI Control applet just has a few new adjustments added.

I have no clue if i installed it right, or if im getting anywhere.  I also reconfigured xserver-xorg to get my resolutions and refresh rates correct.

Can someone help me out?
Heres my .conf file information
Thanks!

> Section "Files"
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
	Identifier	"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver		"fglrx"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"A70-2"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-180
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor		"A70-2"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
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

---

### Post by adam.tropics on 2006-07-02
I had issues with that driver, and had to return to the fglrx from the repos to get xgl back up and running. Try [this link, it seems to work for most people.]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")....Method 1

---

### Post by richbarna on 2006-07-02
Looks fine to me, take a look at this "howto ati mesa problem":-
[http://ubuntuforums.org/showthread.php?t=143283&highlight=howto+ati+mesa+problem]("http://ubuntuforums.org/showthread.php?t=143283&highlight=howto+ati+mesa+problem")

---

### Post by TorxT3D on 2006-07-02
I must say, this is impressive!
I dont know if i have 3d acceleration enabled, ive searched the forums but couldnt find out.

The only annoyances i have is, upon bootup theres an ugly splash of gray twice, then it goes into the desktop, is this normal?

and the tooltips and popup boxes are wavy, that is annoying.  How do i disable that?  I installed gset-compiz but couldnt figure out what plugin it is or how to disable it.

Thanks!!

---

### Post by richbarna on 2006-07-02
Here is a compiz page, it is for Gentoo, but all the info for compiz is the same as Ubuntu.
[http://gentoo-wiki.com/Compiz]("http://gentoo-wiki.com/Compiz")

---

