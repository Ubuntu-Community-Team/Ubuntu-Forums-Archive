---
title: "synaptic touchpad."
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by ataranea on 2007-02-13
i have the driver for the touchpad, iam able to use the touchpad and everything...but i dont have any options menu for the touchpad...i want to disable the "tapping" of this so i wont have to accidently press things. like iam now. anyone able to point in the right directions.

---

### Post by tkjacobsen on 2007-02-13
Just add 
Option		"MaxTapTime"		"0"
to the right place in /etc/X11/xorg.conf, like this:

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"MaxTapTime"		"0"
EndSection

```

Then reboot  (or just restart the xserver)

---

### Post by ataranea on 2007-02-13
um thanks but you would have to be more detailed in where to go...this is still my first day ever using linux

---

### Post by ataranea on 2007-02-13
wondering if there some kind of GUI window menu that would allow me to change the tapping.

---

### Post by tkjacobsen on 2007-02-13
sorry, didn't know that.

I don't know if there is an easy GUI way to do this, so I will guide you through my way.

Open a terminal (Applications -> Accessories -> Terminal)

type "sudo gedit /etc/X11/xorg.conf"

Find a section named: Section "InputDevice" 

which contains a line like; Identifier "Synaptics Touchpad"
or: Driver "synaptics"
Something with synaptics..
Just before the EndSection
add the line:
	Option		"MaxTapTime"		"0"

save + exit

Then just reboot your computer..

Sorry for the slow reply, but I've been at the university all day.

---

### Post by Tmi on 2007-02-13
Since you are new a good tip is to always, and I stress: always, backup your xorg.conf before modifying it, however simple it might seem. This is because that file contains much important data, if you fiddle around with something you are unsure of you might end up with a non-working X alltogether, and then you'll be really gratefull when you rememeber you made a backup before editing the file :). 

Making a backup is really easy;
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
(cp is the command to copy)

If your edit turned out to screw up your system you just
sudo rm /etc/X11/xorg.conf
(rm = remove)
sudo mv /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
(mv = move, works for renaming a file)

After a reboot you will be back in your working system and can now continue experimenting with the file, doing a new backup before the next edit etc.

---

