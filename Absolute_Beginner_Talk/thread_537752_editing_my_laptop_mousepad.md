---
title: "editing my laptop mousepad"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by twistedbydesign on 2007-08-29
How would i go about changing the settings so that when i am using the built in laptop mousepad i can deactivate the tap feature? (so that when i am moving the mouse it isnt trying to click everything i scroll over) I know ho wto do it in windows...but i wasnt sure about ubuntu

---

### Post by tyggna1 on 2007-08-29
If I had my wife's computer I could be more helpful, as she has a touch pad on her's.  If I remember correctly, the settings for that should be under system->preferences-><something> touchpad.  That will let you customize how a touch pad works.  When I get my wife's computer back--I'll let you know for sure.

---

### Post by ThrobbingBrain66 on 2007-08-29
> **twistedbydesign said:**
> How would i go about changing the settings so that when i am using the built in laptop mousepad i can deactivate the tap feature? (so that when i am moving the mouse it isnt trying to click everything i scroll over) I know ho wto do it in windows...but i wasnt sure about ubuntu

Open your xorg.conf file:
```
gksudo gedit /etc/X11/xorg.conf
```

Find the section relating to your touchpad. It looks like this:
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	**Option		"MaxTapTime"		"0"**
EndSection
```

Add the line in BOLD to the section, and restart X (Ctrl+Alt+BkSp).  Log in and tapping should be disabled.  If it's not, you may have to actually restart.

---

### Post by twistedbydesign on 2007-08-29
For some reason whenever i try gksudo /etc/X11/xorg.conf it asks for my password but never actually opens anything..? 
I have a mouse so it's really not a HUGE issue either way...just something thatd be nice to be able to control and deactivate. If you have any more info let me know
thanks guys!

---

### Post by ThrobbingBrain66 on 2007-08-29
ahhh!! I'm sorry, the command should be
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by anewguy on 2007-08-30
Why isn't gsynaptics being referred?  Just install gsynaptics, and add the line:

Option  "SHMConfig"  "true"

under the touchpad section of xorg.conf

when you restart you will be able to configure your touchpad via system/preferences/touchpad using a full configuration utility.:)

---

