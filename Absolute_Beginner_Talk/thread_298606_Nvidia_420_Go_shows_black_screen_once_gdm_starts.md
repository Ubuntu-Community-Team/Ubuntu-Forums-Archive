---
title: "Nvidia 420 Go shows black screen once gdm starts"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-11-13
I've got the 1.0.9629 driver installed on my toshiba satellite 6100 with an 
Nvidia 420 Go video card. When it gets to the gdm, the screen goes black and 
I can hear the audio still going. If I type in my username and password, it
proceeds to log in, but still no video.

This is the closest I've gotten it to work since X used to just break.

```

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
	Identifier	"NVIDIA Corporation NV17 [GeForce4 420 Go]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 420 Go]"
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

```

---

### Post by catanzag on 2006-11-13
If you check the 4th post of [http://www.ubuntuforums.org/showthread.php?t=281823](http://www.ubuntuforums.org/showthread.php?t=281823) you can see that this seems a common problem; if you stay tuned on that thread maybe someone could find the solution (or have already done, I haven't check the whole thread).

regards

catanzag

---

### Post by shanepardue on 2006-11-13
Yeah, I knew it was somewhat of a common problem, but I was seeing if anyone 
had found a solution. This has been a problem with this video card for a long
 time now. Hopefully we'll get a fix soon!

---

### Post by catanzag on 2006-11-13
Maybe are you using compiz (or in general composition is enabled)? there is another suggestion in the 4th step of the howto (first post) in this thread [http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851) concerning blank screen on login.

I'm interest too in solving this problems, my notebook has the same card and in a few time I'll move to Edgy; it's good, but it is a bit unlucky, as it had other troubles in the past with the black vertical lines (EDID problem) and tvout (which still doesn't work for me)

---

### Post by shanepardue on 2006-11-13
Yeah, I have tried a lot of things to get it working both on Dapper
 and on Edgy. Doesn't look like there's a fix.

---

### Post by catanzag on 2006-11-14
OK, we have to wait for a fix. BTW, I forgot to cite this thread [http://www.nvnews.net/vbulletin/showthread.php?p=1056053&posted=1#post1056053](http://www.nvnews.net/vbulletin/showthread.php?p=1056053&posted=1#post1056053) on the nvidia linux forum; user *netllama* (from nvidia) said that 9629 has a bug for all GPUs older than NV3x, and he suggested to downgrade to 9626 or 8776. When I have some spare time (maybe next weekend) I'll try 9626 on Dapper

regards

---

### Post by jarocooke on 2006-11-14
Hi I had a similar problem (exactly the same simptoms) on my laptop which has a nvidia 440 GO graphics card.

Unfortunately I am not 100% sure exactly what I did to make it work, but I can point you in the right direction.

Basically..... actually I am just going to swap over to the laptop and cut out some of the guess work, continued in a minute.

---

### Post by jarocooke on 2006-11-14
As promised mere minutes ago.....

> Section "Screen"

#    Option "DisableGLXRootClipping" "True"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
[B]    Option         "UseDisplayDevice" "DFP"
    Option         "IgnoreDisplayDevice" "CRT"
    Option         "ExactModeTimingsDVI" "TRUE" 
    Option         "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"[/B]
    SubSection     "Display"
        Depth       1
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection


The above is the screen section of my xorg.conf file.  The bolded bits are the bits that I needed to add in order to get it work and I found out about adding these from a web page linked to from the Beryl howto post.  The link is below:

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

I remember that at first I also patched my Nvidia drivers to undo a change in one of its modules, I can find that patch for you if you'd like, but I have since upgraded to the final release of the Nvidia's drivers and haven't applied the patch and all is still working fine here.

I don't think there was anything else that I did, oh there was one other step though.  You need to add 

> options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=1


to the bottom of your /etc/modprobe.d/options file.

Anyway if in doubt all this in contained within troubleshooting point 7 of the webpage linked to above.

Good luck let me know how you get on.

---

### Post by jarocooke on 2006-11-14
One last thing, now that I think about it I think the magic ingredient out of all of this (at first following the instructions on the howto webpage I previously linked to, didn't work, even with the patch applied) was the addition of ```
Option "IgnoreDisplayDevice" "CRT"
```

I suppose I shouldn't be so lazy and just find out which bit was the bit that made the difference (or maybe it was all of it), but at the end of the day you know what they say **if it ain't broke, don't fix it**. :-D 

I'd be interested to see if any of this helps you as it does appear to be a fairly common problem and I couldn't find a definitive fix when I was looking.

---

### Post by catanzag on 2006-11-15
Many thanks jarocooke for posting your working xorg.conf. Basically, the bolded lines are the same I have in mine, in order my 8776 version work, so I have to add only
```
Option "AddARGBGLXVisuals" "True"
```
I'll see when my babies let me try it ;)
just a question, I noted you're an Edgy user, but which nvidia driver are you using? I mean, if you're using 9629, did't you get the troubles explained in my post #6?

regards

---

### Post by catanzag on 2006-11-15
shanepardue, somewhere in forums I found a reported blank screen on old cards before X restarting because eeprom module loading; the suggested solution is either to comment it out from /etc/modules or to rmmod it.

Hope it could help you.

---

### Post by catanzag on 2006-11-17
OK, my last post in this thread, at least for now. I tried 9626 and got blank screen; from Xorg.0.log I noticed that driver wanted to output to CRT, so I added to xorg.conf ```
Option "IgnoreDisplayDevice" "CRT"
``` (thanks jarocooke!!!); then out was to LCD, but only coloured spots or 1-2 pixel random coloured vertical stripes were shown.

I made a tour on [http://www.nvnews.net/](http://www.nvnews.net/) forums, and lot of threads dealing with this issues, confirmed by NVIDIA registered users, that there are some bugs on this family of drivers, ranging from the incompatibility with old (?) cards up to erroneous ram management even in more recent ones (6600 with TurboCache). 

I'll try a couple of things, but I probably I'll go back to 8774 with XGL, till  functionality won't be fixed.

---

