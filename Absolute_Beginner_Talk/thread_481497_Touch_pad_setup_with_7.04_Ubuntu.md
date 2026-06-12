---
title: "Touch pad setup with 7.04 Ubuntu"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by lawentzel on 2007-06-22
I liked the features of previous Ubuntu's for my laptop where you could drag your finger and have a webpage scroll. With 7.04 they no longer have that feature.  So, I've installed "Touchpad" and when I run it, I am getting the following error.

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

I want to say I have looked for SHMConfig in xorg.conf and it wasn't there.  So, what do I do to enable the touch pad features?  Thanks.

---

### Post by bren on 2007-06-22
i have the exact same problem

bren

---

### Post by annda on 2007-06-22
you have to add this line to your xorg.conf

Option "SHMConfig" "true"

in the touchpad section. specifying "Synaptics" as driver is a good idea too.

---

### Post by kerry_s on 2007-06-22
you need to add that option yourself.

sudo gedit /etc/X11/xorg.conf

my xorg.conf, mine is alps, i use> syndaemon -d <in my startup it disables the touchpad whem i type

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"TouchpadOff"		"0"
# 0 Touchpad is enabled 
# 1 Touchpad is switched off 
# 2 Only tapping and scrolling is switched off

	Option		"AccelFactor"		"0.050"
	Option		"MaxTapTime"		"160"
	Option		"MaxTapMove"		"500"
	Option		"SHMConfig"		"on"
	Option		"RBCornerButton"	"2"
	Option		"LockedDrags"		"true"
EndSection

```

---

### Post by lawentzel on 2007-06-22
Going into my xorg.conf I did not have anything dealing with "Synaptics Touchpad"  So, I copied and added the following lines immediately above my "waco" lines.

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SHMConfig"		"true"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection
```

Afterwards I restarted my computer. When I tried to run the program again to set things up got the same error.  I also looked in System, Preferences, Hardware Information.  I assumed incorrectly apparently that Synaptics Touchpad would appear.  It didn't.  So... I am still needing help.  Thanks.

---

### Post by lawentzel on 2007-06-22
kerry_s I have copied your code, and put it in my xorg.conf and it still does not work.  I didn't do a Control + Alt + Backspace this time.  I actually did a complete restart.  Still not working.

---

### Post by kerry_s on 2007-06-22
sudo dpkg-reconfigure -phigh xserver-xorg

run this to redo your xorg.conf, something is messed up. then logout and ctrl+alt+backspace

also make sure you instll "mc" in case something goes wrong, it makes it alot easier if you get stuck with out X

sudo apt-get install mc

if you get stuck at command line login and type> sudo mc <use> mc if you don't need root access. :)

---

### Post by lawentzel on 2007-06-29
Kerry, that didn't work.  Here is what did.

I was also interested in trying KDE on my system.  So I installed KDE along with Gnome.  Now the touch pad works perfectly.  I have no idea why.  But it does.

---

