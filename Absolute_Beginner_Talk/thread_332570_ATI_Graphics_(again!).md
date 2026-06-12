---
title: "ATI Graphics (again!)"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by mells on 2007-01-06
Hi Guys

I'm almost at my wits end with my laptop and Edgy. I am trying to get 3D acceleration working again. I had it working first time with easyubuntu but had to reinstall the system. My laptop (Compaq n1020v) doesn't like the new release of easy.

I have installed the ati drivers manually following several guides; most recent 
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) 

......but X keeps crashing. I keep getting the message

"NO SCREENS" at the bottom of the error report.

Here is my Xconf, can someone have a look at give me a pointer. I dont want this to beat me! lol!

> Section "Files"
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
	Identifier	"ATI RADION 340M"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADION 340M"
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
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Please help ;)

---

### Post by mells on 2007-01-06
anyone?

---

### Post by ajgreeny on 2007-01-06
Sorry I can't help any more than to tell you, just in case yopu haven't noticed, that in spite of installing the fglrx driver on your machine, that is not the one being used at the moment, you still have the open source ati driver.

Quote from your xorg.conf
Section "Device"
	Identifier	"ATI RADION 340M"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

I had the same problem with dapper and eventually gave up and stuck with the ati OSS driver, which does give me acceleration,but perhaps only software as opposed to hardware, (that's as I understand it, anyway).  I'm not a gamer so it doesn't matter to me, and I'll just wait until AMD/ATI get their act together with easily installed drivers.

---

### Post by mells on 2007-01-06
thanks if I change 'device' from "ati" to "fglrx" it crashes X. 

I only want to get Beryl working again....

---

### Post by Houman on 2007-01-06
sorry I Cant help either but I just wanted to give it a shot,

I think there must be something wrong with your xorg.conf , so I am going to try and guess at it:

1- the link you provided for the driver installation asks that you disable composite kayout, this section was missing from your xorg.conf:

Section "Extensions"
	Option "Composite" "disable"
EndSection

2-shouldnt the device section have "fglrx" like (this is my xorg): *[update: I just realied ajgreeny mentioned this while i was writing my post :P]*
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
.........
EndSection

But yours lists ati not fglrx as the driver. you could try running "sudo dpkg-reconfigure xserver-xorg" and select fglrx in the driver section instead of ATI.


also can you post the output of "cat /var/log/Xorg.0.log | grep EE"?
also why did you use the manual way? the guide you provided has a much easier way listed, doing things the hard was is always a source of problems.

regards

Houman

---

### Post by petermck on 2007-01-06
Have a look at [http://www.ubuntuforums.org/showthread.php?t=321766&highlight=howto+ati](http://www.ubuntuforums.org/showthread.php?t=321766&highlight=howto+ati) .
This worked for me, but unless your graphics card has it's own memory don't bother with the stuff about Beryl. I tried for two days to get it working on a ATI Xpress 200M without success.
The good news is the 3D stuff works great (Google Earth for example) and the first bit of the guide about installing the ATI proprietry fglrx driver worked well.

---

### Post by mells on 2007-01-06
thanks for your help. I've made the changes suggested. I'll reboot and see it works.

---

### Post by mells on 2007-01-06
hurarh! it booted without crashing X but I still havent got direct rendering...](*,) 

carl@Angel:~$ glxinfo | grep "direct rendering"
direct rendering: No
carl@Angel:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20060327 AGP 4x NO-TCL
OpenGL version string: 1.2 (1.3 Mesa 6.5.1)

---

### Post by Kubunteando on 2007-01-06
I would say, you may have already Direct Rendering working with the Open Source drivers.

Try "glxinfo | grep -i render". If you get "Direct Rendering" as "yes", you have HW acceleration enabled.

If not I suggest you check the troubleshooting section on [http://dri.freedesktop.org](http://dri.freedesktop.org).
The first try is to "export MESA_DEBUG=true", and then "glxinfo". Check the error messages you may get with the troubleshooting guide.

When MESA appears in the "fglrxinfo" it does not mean the DRI is not enabled.
MESA supports also DRI and can perform even better than the "fglrx" driver for some of the ATI cards, especially the ones not supported on the ATI drivers newer then the 8.28.8 version.

It seems that in MESA 6.5.2 they work even better,

You can check if your card has the ATI HyperZ feature, and you can enable it on the configuration tool "driconf". You can install it from the Ubuntu repositories. That increases the performance by about 40%.

---

### Post by Kubunteando on 2007-01-06
Sorry. I just did a quick reading. According to the output of "glxinfo" Direct Rendering is off.
You can heck the Troubleshooting section on the link above.

If you get errors on the libGL... you may need to compile the MESA 6.5.1 to get the libGL...
The info is on the "buiding" section of [http://dri.freedesktop.org](http://dri.freedesktop.org).
You may get MESA 6.5.1 from [www.mesa3d.org](www.mesa3d.org)

---

