---
title: "dell 2007wfp as external monitor with 1st gen black macbook"
date: 2007-04-08
forum: Apple Intel Users
---

### Post by ryan86corolla on 2007-04-08
Hi, I can't seem to get my Dell 2007WFP working at all with my macbook. I've fixed my xorg.conf according to [the wiki]("https://help.ubuntu.com/community/MacBook") and tried screwing around with it a bit but to no avail. Here's my xorg.conf:
```
######################################################################
Section "ServerFlags"
#       Option          "DefaultServerLayout" "Default Layout"
#       Option          "DefaultServerLayout" "MonitorLayout Layout"
#       Option          "DefaultServerLayout" "Clone Layout"
       Option          "DefaultServerLayout" "Xinerama Layout"
#       Option          "DefaultServerLayout" "DELL 2007WFP Layout"
EndSection
######################################################################
Section "Device"
        Identifier      "MonitorLayout Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "MonitorLayout" "NONE,CRT+LFP"
EndSection

Section "Screen"
        Identifier      "MonitorLayout Screen"
        Device          "MonitorLayout Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "MonitorLayout Layout"
        Screen          "MonitorLayout Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "Device"
        Identifier      "Clone Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "MonitorLayout" "CRT,LFP"
        Option          "Clone"
EndSection

Section "Screen"
        Identifier      "Clone Screen"
        Device          "Clone Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Clone Layout"
        Screen          "Clone Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "Device"
        Identifier      "Xinerama Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Screen          0
        Option          "MonitorLayout" "CRT,LFP"
EndSection

Section "Device"
        Identifier      "Xinerama Device (2)"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Screen          1
        Option          "MonitorLayout" "CRT,LFP"
EndSection

Section "Screen"
        Identifier      "Xinerama Screen"
        Device          "Xinerama Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Xinerama Screen (2)"
        Device          "Xinerama Device (2)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1680x1050"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Xinerama Layout"
        Screen          "Xinerama Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        # RightOf LeftOf Above Below
        Screen          "Xinerama Screen (2)" RightOf "Xinerama Screen"
        Option          "Xinerama"
EndSection

Section "Monitor"
        Identifier      "DELL 2007WFP"
        Option          "DPMS"
        HorizSync       30.0-83.0
        VertRefresh     56.0-76.0
EndSection

Section "Screen"
        Identifier      "DELL 2007WFP Screen"
        Device          "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Monitor         "DELL 2007WFP"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1680x1050 at 60" "1280x1024" "1152x864"
"1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"DELL 2007WFP Layout"
	Screen		"DELL 2007WFP Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
######################################################################

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Option		"XkbOptions"	"lv3:ralt_switch"
	Option		"XkbVariant"	"mac"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```
Now, I can run in clone and xinerama layouts fine - clone simply runs the Macbook screen at native resolution while the 2007WFP stays black and tells me there's no input when I turn it off/on. Xinerama, though, gives me (I think) 1680x1050 resolution on the macbook screen, while the 2007WFP stays black just like in clone layout. Check out [this screenshot]("http://i15.tinypic.com/4c1jfo2.png") to see what I mean - see the workspacer switcher on the bottom right? The firefox window is maximized but there's extra room below and to the right of it. I even have  a terminal window open to the right there, completely off the screen. I can move my mouse past the right edge of, but not under, the macbook screen for some reason.

And the screenshot is even screwy - it's resolution is apparently 1600x640 although the area I can see is 1280x800, as you can tell.

Again, this weird resolution only happens with xinerama. I'd ideally like to be able to run only the 2007wfp and just leave the macbook screen off - that way I could enable beryl, and when I wasn't near my external monitor, I'd just run the default layout. Although xinerama might be nice occasionally too. But in any case, my dell 2007wfp is not showing anything at all right now.

Any thoughts or suggestions are greatly appreciated. If you need any other information, I'll be glad to provide.

---

### Post by Meck1982 on 2007-04-20
Hi,

first of all: Your are not alone out there. For now external monitor support in linux is pretty shitty. Well it works, if you know HOW. I managed to get my MacBook working with my Eizo FlexScan L778 in 1280x1024 over a mini-DVI-to-DVI adapter in the way, that my MacBook monitor stays black. So I could use beryl and this stuff... was pretty cool. The bad thing is: I did not save my xorg.conf and made a fresh feisty install yesterday. Now I am freaking out, because I just cannot get working any more - External monitor works fine with 1024x768, but not with 1280x1024 (shows a very flickering unusable image).

But now to your problem: Your configuration file looks pretty messy. If you want to go for the single-external-monitor-with-beryl option I would recommend you to get a fresh xorg.conf by running dpkg-reconfigure xserver-xorg. Put the resolution of your external monitor when asked. After that edit the config and add in the device section the following line:

Option "MonitorLayout" "CRT+DFP"

This should turn on both digital and analog external monitors on Pipe A.
Hope this works -- Good Luck!

PS: Has anybody out there a dvi monitor with 1280x1024 running without internal macbook display on? I do not like this dual/multihead/xinerama stuff, because the macbook monitor is pretty shitty compared to my other display and I like beryl.

---

### Post by ryan86corolla on 2007-04-21
Hey, thanks a lot. That line did enable my external monitor. Unfortunately, I can't seem to get it at it's native 1680x1050 resolution - it stays at 1024x768 at 75hz. It should be 1680x1050 at 60hz. Here's my xorg.conf:
```
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
	Option		"XkbOptions"	"lv3:ralt_switch"
	Option		"XkbVariant"	"mac"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option "MonitorLayout" "CRT+DFP"
EndSection

Section "Monitor"
        Identifier      "DELL 2007WFP"
        Option          "DPMS"
#	Modeline "1680x1050" 148.5 1680 1784 1960 2240 1050 1053 1059 1089
EndSection

Section "Screen"
        Identifier      "Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Monitor         "DELL 2007WFP"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1680x1050 at 60" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```
The "at 60" part after the resolution doesn't seem to change anyting, my screen resolution preference dialog still tells me it's at it's maximum resolution of 1024x768 at 75hz. Also the modeline doesn't seem to change anything either. Any ideas how to achieve 1680x1050 resolution here?

---

### Post by m0se5 on 2007-04-21
```

DefaultDepth    24
        SubSection "Display"
                Depth            24
                Modes           "1680x1050@60"
        EndSubSection

```

---

### Post by ryan86corolla on 2007-04-21
> **m0se5 said:**
> ```

DefaultDepth    24
        SubSection "Display"
                Depth            24
                Modes           "1680x1050@60"
        EndSubSection

```

That didn't change anything. :( It's still just 1024x768 at 75hz. 

I checked /var/log/Xorg.0.log and found this interesting:
```
(II) I810(0): Not using mode "1680x1050@60" (no mode of this name)
```

and this when i changed it:
```
(II) I810(0): Not using mode "1680x1050" (no mode of this name)
```

although it also has this earlier:
```
(II) I810(0): Display Info: DFP (digital flat panel): attached: TRUE, present: TRUE, size: (1680,1050)
(II) I810(0): Display Info: LFP (local flat panel): attached: TRUE, present: TRUE, size: (1280,800)
(II) I810(0): Display Info: Second (second CRT): attached: FALSE, present: FALSE, size: (0,3087)
(II) I810(0): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,3087)
(II) I810(0): Display Info: DFP2 (second digital flat panel): attached: FALSE, present: FALSE, size: (0,3087)
(II) I810(0): Display Info: LFP2 (second local flat panel): attached: FALSE, present: FALSE, size: (0,3087)
(II) I810(0): Size of device DFP (digital flat panel) is 1680 x 1050
(II) I810(0): Currently active displays on Pipe A:
(II) I810(0):   CRT
(II) I810(0):   DFP (digital flat panel)
(II) I810(0): Lowest common panel size for pipe A is 1680 x 1050
(II) I810(0): No active displays on Pipe B.
(==) I810(0): Display is using Pipe A

```

and this...
```
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 720x400@70Hz
(II) I810(0): 640x480@60Hz
(II) I810(0): 640x480@75Hz
(II) I810(0): 800x600@60Hz
(II) I810(0): 800x600@75Hz
(II) I810(0): 1024x768@60Hz
(II) I810(0): 1024x768@75Hz
(II) I810(0): 1280x1024@75Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported Future Video Modes:
(II) I810(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) I810(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 119.0 MHz   Image Size:  434 x 270 mm
(II) I810(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) I810(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) I810(0): Serial No: HF7306CI183L
(II) I810(0): Monitor name: DELL 2007WFP
(II) I810(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 83 kHz, PixClock max 140 MHz

```

and this:
```
(II) I810(0): Printing DDC gathered Modelines:
(II) I810(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) I810(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) I810(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) I810(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) I810(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) I810(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) I810(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) I810(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) I810(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) I810(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) I810(0): Modeline "1680x1050"  119.00  1680 1728 1760 1840  1050 1053 1059 1080 -hsync +vsync

```

I'm not sure what all this means, but I see in several places the right resolution (1680x1050@60hz) recognized. Can anyone help? Thanks again.

this must be where things go wrong, but I'm not sure what to do about it.
```
(II) I810(0): DELL 2007WFP: Using hsync range of 30.00-83.00 kHz
(II) I810(0): DELL 2007WFP: Using vrefresh range of 56.00-76.00 Hz
(II) I810(0): Not using mode "1680x1050" (no mode of this name)
(II) I810(0): Not using built-in mode "1280x1024" (width too large for virtual size)
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0): *Built-in mode "800x600"
(**) I810(0): *Built-in mode "640x480"
(**) I810(0): Display dimensions: (430, 270) mm
(**) I810(0): DPI set to (60, 72)

```

---

### Post by ryan86corolla on 2007-04-21
I just got 1280x800 mirrored with my Macbook display by doing this, from [this thread]("http://ubuntuforums.org/showthread.php?t=326211&page=2"):
```
I managed to solve this problem for myself by installing xserver-xorg-video-intel (universe) which appears to be a build of the experimental modesetting branch of the driver. This obsoletes 915resolution. Change the driver in xorg.conf to intel (from i810) after installation.
```

Not what I wanted exactly, but a step in the right direction. And now my screen resolution dialog in gnome is this:
[IMG]http://i11.tinypic.com/43nf412.png[/IMG]
The refresh rate's only option is 60hz. I tried 1680x1680, but the area I see stays 1280x800, with the extra pixels existing off-screen, i.e. I can move my mouse past the edge of the monitor. These resolutions are not in my xorg.conf (same as above, except now using "intel" driver instead of "i810"), so I'm not sure how I can change them.

---

### Post by ryan86corolla on 2007-04-22
bump. anyone? The resolution in my xorg.conf is not what's coming out onscreen, and it seems unrelated to what's in my screen resolution prefs. I don't get it. :(

---

### Post by Meck1982 on 2007-04-23
Try changing the MonitorLayout in your device section like this:

        Option          "MonitorLayout" "LFP,DFP"

I know it does not seem to be of much sense, but it did some magic for me: Now I have my external display driven with 1280x1024 (Native res) and MacBook screen stays black, so I can use beryl :P
Would be interesting to hear if it worked for you or not...

---

### Post by thava on 2007-04-23
Hi

Did you get your external monitor dell 2007wfp work properly on your mac book? 1680x1050?

/ Thava

---

### Post by ryan86corolla on 2007-04-23
> Did you get your external monitor dell 2007wfp work properly on your mac book? 1680x1050?

Not yet. I tried this:
> 
Option "MonitorLayout" "LFP,DFP"

but it didn't change anything. :(

For good measure I've attached my xorg.conf and Xorg.0.log. I tried cutting out unnecessary parts of the log to make it under the size limit for txt, but I ended up just gzipping it.

---

### Post by thava on 2007-04-23
Let me know if you find any solutions.

I will not install ubuntu brefore i am sure about i can use my external monitor Dell 2007 WPF with 1680x1050 resolution.

/ Thava

---

