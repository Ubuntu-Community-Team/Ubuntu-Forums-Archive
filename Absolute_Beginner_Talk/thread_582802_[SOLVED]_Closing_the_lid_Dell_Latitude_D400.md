---
title: "[SOLVED] Closing the lid Dell Latitude D400"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by derred on 2007-10-20
I have an old D400 that I use to take Ubuntu with me on the road. I used gutsy tribe 3-5 on it with no problems whatsoever. BUT after 5 I stopped updating daily due to a veeeeery slow network connection. 

On the 18th I did a fresh install of the final 7.10 release only to find I can't close the lid on my laptop anymore. If I do the entire system freezes. No Ctrl+Alt+BkSp, no going to a Ctrl+Alt+F1, no nothing. 

If I close the lid under X11 I just get the mouse cursor at the exact position I'd left it. 
If I close it while in a tty I get a blank screen but the laptop continues to work & if i go to X by Ctrl+Alt+F7 the computer gets the screen back.

I really want to make this work because I use this laptop to take my notes on at college and for some web design on the side. PLEEEEEEEASE!!! I'm desperate.

---

### Post by derred on 2007-10-20
Fixed it! It was the 'intel' driver in "/etc/X11/xorg.conf". What you need to do is simply replace the intel experimental driver with the old, slow but faithful i810 driver.

```
# xorg.conf (xorg X Window System server configuration file)
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
# British layout
	Option		"XkbLayout"	"gb"
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
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
# this works
	Driver		"i810"  
# this doesn't work
#      Driver          "intel" 
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

``` 

I must say that Compiz-fusion is much smother under the other driver and if this was a desktop I would have kept it for sure. As it is a laptop I'll stick with low frame-rates and less eye-candy.

---

### Post by c3007223 on 2007-10-31
Fantastic - Worked like a charm after restart

---

### Post by TheVDM on 2008-01-30
Excellent, just the solution I was looking for, also for any of you guys who's D400 hangs when you go to turn it off, this also sorts that problem... and AWN etc... are still running fine and looking good.

Jym

---

### Post by aaronhall555 on 2008-04-21
Sorry if I'm bringing up an old thread, but I'm new to the Ubuntu forum, and this problem was extremely irritating.

I just wanted to confirm that simply changing the Device driver in the xorg.conf from "intel" to "i810" fix the hanging problem when I closed the lid on my Dell Latitude D500, which also has the 855GM Integrated Graphics Device, also I did not notice a performance drop with Compiz.

Running: Ubuntu 7.10 - the Gutsy Gibbon

Section "Device" from my /etc/X11/xorg.conf:
```

Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "**i810**"
        BusID           "PCI:0:2:0"
EndSection

```

Thank you Ubuntu community!!!

---

### Post by rlondre on 2008-07-20
Hi I would like to know the steps I need to take to replace the drivers. I have a dell d500 and have the same issue closing the lid.

---

### Post by daz23 on 2008-07-23
I fixed the closing lid problem on my Dell D400 by doing the following:

edit the /etc/X11/xorg.conf and add the following line:

  Section "Device"
    ...
    **Option "ForceEnablePipeA" "true"**
  EndSection

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/138256](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/138256)

---

