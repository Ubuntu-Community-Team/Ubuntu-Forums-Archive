---
title: "Speed up cursor"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Padraig1 on 2007-10-25
Hi,
I'm using a touchpad but the cursor speed is very slow, how can I speed this up? The 'sensitivity'  bar in Synaptics Touchpad doesn't seam to have any effect.

Thanks.

---

### Post by atomkarinca on 2007-10-25
if you're using gnome;

system > preferences > mouse > motion tab.

---

### Post by Padraig1 on 2007-10-25
thanks for the reply,
acceleration and sensitivity are set to max, but if I reduce them the cursor doesn't slow

---

### Post by atomkarinca on 2007-10-25
strange. mine does slow down.

you can try this: hit alt+f2 and type gconf-editor. then desktop > peripherals > mouse

on the right tab you will see mouse_acceleration. right-click and select edit key. then try higher numbers and see if it works for you.

---

### Post by Padraig1 on 2007-10-25
still no change,
I see a touchpad folder alongside the mouse folder, do the mouse settings control the speed of cursor even if a touchpad is being used?

---

### Post by atomkarinca on 2007-10-25
i don't know but you can also take a shot at that touchpad folder, it may work.

---

### Post by Padraig1 on 2007-10-25
I tried changing some of the settings in the touchpad folder but still no improvement. I got the following message under 'Key Documentation' when I tried to change the settings:
'This key has no schema'

---

### Post by Padraig1 on 2007-10-26
I'm trying to modify the Synaptics touchpad settings in the  /etc/X11/xorg.conf file now. I've set it to the max speed. I got this info from: 
[http://www.tctwest.net/~mlewis00/XF86Config-4.synaptics]("http://www.tctwest.net/~mlewis00/XF86Config-4.synaptics")


The file is now set to:

[COLOR="Black"]Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
        Option          "SHMConfig"             "on"
	Option		"MinSpeed"		"1.0"                  [COLOR="Navy"]the next three lines are new additions[/COLOR]
	Option		"MaxSpeed"		"1.0"
	Option		"AccelFactor"		"0.2"
EndSection[/COLOR]

The changes are having an affect, the cursor is slower when I'm moving the cursor slowly but no change when I'm trying to move the cursor from one of the screen to the other.

Any help would be great.

---

