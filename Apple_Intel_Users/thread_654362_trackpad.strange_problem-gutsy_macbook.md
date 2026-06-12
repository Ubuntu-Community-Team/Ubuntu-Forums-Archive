---
title: "trackpad.strange problem-gutsy macbook"
date: 2007-12-31
forum: Apple Intel Users
---

### Post by p0rtlandcubsfan on 2007-12-31
i've been trying to enable the trackpad features on my macbook, such as two-finger scrolling and two-finger rightclick, but to no avail.  I keep running into an error - timestamp too far in the future.  I can't seem to reconcile the timestamps between OSX.5 and Ubuntu 7.10 as they dual-boot on my second-gen macbook

any help is most appreciated.  these forums rule.  I was having wireless issues, and now i'm posting wirelessly from inside gutsy.  totally amazing.  screw paying for software.


/.

:popcorn:

---

### Post by erfahren on 2007-12-31
what kind of trackpad? you may have to edit it's section in the /etc/X11/xorg.conf file (back the file up first!)

search for the man page for you trackpad

here's one for Synaptics:
[http://linux.die.net/man/5/synaptics](http://linux.die.net/man/5/synaptics)

here's another thread about it:
[http://ubuntuforums.org/showthread.php?p=4000681](http://ubuntuforums.org/showthread.php?p=4000681)

(note: they're refered to as "touchpads" on PCs, so info referring to that term should be applicable.)

---

### Post by p0rtlandcubsfan on 2007-12-31
it's the touchpad that comes on the current macbook... still can't seem to get it working.  no speed adjustment (that actually speeds up cursor movement instead of just looking like it might but then not) 
no right-click (only has one button and I can't turn on two-finger right-click)
no two-finger scroll (right side up/down scroll works ok, sorta like that which comes on many toshiba notebooks, but way choppier and too sensitive - I can't figure out where to adjust it)
is there any way for me to activate the root account?

sorry kind of a n00b here.  i've worked with linux a little bit before, but not very much so bear with me.

---

### Post by erfahren on 2007-12-31
look in your xorg.conf file for the section on the trackpad. it should list what kind it is.

browse to /etc/X11 and you can open up xorg.conf in the text editor (you can't make any changes to it doing it that way, don't worry)

my section looks like (I have everything disabled, I'm too clumsy - lol):
```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
        Option          "VertEdgeScroll"        "0"
	Option		"MaxTapTime"	"0"
	Option		"SHMConfig"	"on"
EndSection

```

---

### Post by p0rtlandcubsfan on 2007-12-31
i seem to have gotten it working, thanks for your help

---

