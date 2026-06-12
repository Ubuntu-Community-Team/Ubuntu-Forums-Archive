---
title: "I've lost the vertical scroll on my touchpad"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-01-24
I don't know why, but I've lost the vertical scroll function on my laptop touchpad, and I'd really like to have it back. Here is the relevant section of my xorg.conf file; maybe someone can tell me what's missing or incorrect:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"VertScrollDelta"	"50"
	Option		"HorizScrollDelta"	"30"
	Option		"MinSpeed"		"0.4"
	Option		"MaxSpeed"		"0.5"
	Option		"AccelFactor"		"0.0020"
EndSection
```

Thank you!!

---

### Post by p_quarles on 2008-01-24
I had that happen once, but restarting the X server took care of it. If you've already tried that, let me know. I can bootup the laptop and take a look at the config.

---

### Post by doctorbighands on 2008-01-24
I've tried restarting X, and then re-restarting X. So far, no luck.

---

### Post by p_quarles on 2008-01-24
Well, mine is the same as yours, minus the last five lines you listed (i.e., they just don't exist). Of course, this is a Compaq laptop, so it may be that those settings are required for your hardware. You could back up the file, delete those lines, and restart X to see if that makes any difference.

Another thing to check is the section right above synaptics, since I believe that the "configured mouse" device also affects the way the touchpad operates. The "ZAxisMapping" option (the part that controls the scroll wheel on mice) should be "4 5". 

If that's good, I guess I'd just ask if you've used any configuration software for the touchpad. There was recently an Xorg update, and that may (?) have broken something that was set with a GUI app. Finally, 
if you have anything in ~/.Xmodmap (you won't by default), that could be affecting the touchpad.

---

### Post by doctorbighands on 2008-01-24
Those last five lines are what keeps my cursor traveling at a reasonable speed. If they aren't there, my cursor moves as if it's dragging through mud.

My ZAxisMapping setting is "4 5", and there's nothing in ~/.Xmodmap.

I haven't used any configuration software for the touchpad other than the standard Gnome GUI app (System -> Preferences -> Mouse). I only got into the xorg.conf file after I suddenly lost my scroll function.

*sigh*...

Thank you for all of the ideas, though!

---

### Post by p_quarles on 2008-01-24
> **doctorbighands said:**
> I haven't used any configuration software for the touchpad other than the standard Gnome GUI app (System -> Preferences -> Mouse).
Well, maybe it's time you tried another one. ;)

First, you'll need to add a line to the end of the "Synaptics Touchpad" section of xorg.conf:
```
Option        "SHMConfig"          "on"
```
(of course, please back up xorg.conf before doing this)
Restart X so the change takes effect. Now, install the GUI config tool:
```
sudo apt-get install qsynaptics
```
This will give you an easier way of modifying the settings, and hopefully can restore the vertical scroll.

---

### Post by doctorbighands on 2008-01-25
No matter what I try in Qsynaptics, I can't enable the vertical scroll. I've even tried something as counterintuitive as unchecking the vertical scroll box!

Needless to say, I'm beginning to suspect the touchpad itself...

---

