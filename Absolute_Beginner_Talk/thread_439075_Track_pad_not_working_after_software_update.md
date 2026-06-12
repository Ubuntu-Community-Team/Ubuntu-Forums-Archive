---
title: "Track pad not working after software update"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by leefischer on 2007-05-10
I have a compaq presario V5000.  It has a track pad that has a little section on the bottom and one side that functions like a mouse wheel when you run your fingers along it.    i just installed Ubuntu a couple of days ago and the trackpad was working fine.  I just did a software update and the trackpad has lost all features.  It is now just a point and click device.   I cannot even double tap it and drag a selection box around anything.    This i happening on the desktop, firefox and everything.

Has the software update changed something which, as a result, has stopped the trackpad from operating as it used to?  Is there some kind of system restore in Ubuntu?   Any ideas?   When i first installed Ubuntu 7.04 all was cool!


Cheers, Lee from New Zealand

---

### Post by diatribe on 2007-05-10
if its a synpatics pad, you may have to edit /etc/X11/xorg.conf so it recogises the synaptics driver

---

### Post by Franko30 on 2007-05-12
> **diatribe said:**
> if its a synpatics pad, you may have to edit /etc/X11/xorg.conf so it recogises the synaptics driver

Hi,

**if have a similar problem:**
I installed 7.04beta on my laptop and the touchpad was a simple click and point device - even after the upgrade to 7.04 final. The isn't even a section for Synaptics in the xorg.conf...

**But:**
When doing a fresh install of 7.04 all the features (like double click and hold, scroll with sliding along the richt side of the touchpad etc.) just work. The Synaptics option is present in the xorg.conf

**Now the problem:**
I had to do a reinstall 'on the road' and only had 7.04beta available and then i upgraded to 7.04 resulting in the above mentioned problems.

[B]Simply (manually) inserting a Synaptics section in the xorg.conf doesn't help.
[/B]
**The question:**
How can I force another hardware detection or the like that might find the touchpad and insert the necessary section in the xorg.conf automatically?

Cheers

Frank

---

### Post by Franko30 on 2007-05-13
Anyone?

Thanks

Frank

---

### Post by jkblacker on 2007-05-13
I have 'Trackpad' installed from Add/Remove which has options to enable scrolling (both horizontal, vertical as well as circular) and tapping. I guess this might help?

---

### Post by Franko30 on 2007-05-14
> **jkblacker said:**
> I have 'Trackpad' installed from Add/Remove which has options to enable scrolling (both horizontal, vertical as well as circular) and tapping. I guess this might help?

Hi there,

and thanks for the reply.

But unfortunately this doesn't work - gsynaptics complains that there is no 'SHMconfig = true' line in the xorg.conf.

This means: There already has to be a Synaptics section in the xorg.conf for gsynaptics to work. But even when I put that line in manually (with scrolling options etc. enabled) the touchpad is still working only as a 'click and point' device.

Therefore my conclusion that it isn't recognised in my post above.

Cheers

Frank

---

### Post by Franko30 on 2007-05-14
**[SIZE="2"]Mea Culpa - I'm so dumb![/SIZE]**

I just forgot to insert something in the xorg.conf:

I insterted the necessary Synaptics section, but didn't insert

```
InputDevice	"Synaptics Touchpad"
```

in

```
Section "ServerLayout"
```

thus the touchpad wasn't used with all its features...

So, for everybody who has problems after some 7.04 Feisty updates, the necessary Section looks like this:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection
```

**plus there's the entry in the Server layout Section...**

If you want to get rid of those problems with a 'jumping cursor' while editig text (because you accidently brushed the touchpad) use **syndaemon** to **disable your touchpad while typing**. A HowTo for this can be found here:

[http://ubuntuforums.org/showthread.php?t=271052](http://ubuntuforums.org/showthread.php?t=271052)

Cheers

Franko30

---

### Post by mkeithcloud on 2008-04-18
I have a similar problem with my Acer 5670. The tracking pad does not work at all after I did all the software updates. I am fairly new new to Linux so this may be a dumb question. I tried Franko30's advice about editing xorg.conf but I am unable to do so because 'root' is the owner. After poking around a few user and group settings I am still unable to figure out how to be able to access/edit system files, or log in as root onto the system. Please help.

***I am a huge fan of Linux and Ubuntu and would love to get to know how use this distribution!

---

### Post by Franko30 on 2008-04-21
[QUOTE=mkeithcloud;4741650editing xorg.conf but I am unable to do so because 'root' is the owner.[/QUOTE]

Use the "sudo" command to execute a program as root. For instance "sudo nano /etc/X11/xorg.conf"


But beware: You can seriously damage things, so make backups of the files you edit before you save any changes!!!

Cheers

Franko30

---

