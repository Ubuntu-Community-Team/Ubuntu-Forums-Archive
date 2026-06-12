---
title: "screen resolution"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by LookTJ on 2007-03-24
Part of my xorg.conf
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x960"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x960"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x960"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x960"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x960"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x960"
        EndSubSection
```What I am trying to acheive is 1280x960. I tried restarting gdm, rebooting computer, restarting xorg.

But I still get 1024x768(screenshot attached)

Note: Feisty Beta Gnome

---

### Post by annda on 2007-03-24
do you have the drivers for your graphic card installed? the default driver may not handle the resolution.

what is your card?

---

### Post by LookTJ on 2007-03-24
> **annda said:**
> do you have the drivers for your graphic card installed? the default driver may not handle the resolution.

what is your card?
ATI Radeon 9000

---

### Post by annda on 2007-03-24
try those steps i posted for someone else using KDE, so in the last command substitute 'gedit' for 'kate':

[http://ubuntuforums.org/showpost.php?p=2333304&postcount=2](http://ubuntuforums.org/showpost.php?p=2333304&postcount=2)

i hope this helps.

---

### Post by khedron on 2007-03-24
Which driver are you using, the open-source ati one or the proprietary fglrx one? You can go into xorg.conf to find out. The relevant section is the one that looks like this:
```

Section "Device"
        Identifier      "ATI RADEON X800"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

```

---

### Post by eldragon on 2007-04-20
im having the exact same problem with fglrx drivers, feisty, and refresh rate.... and the card is a x600 ati radeon

under edgy, ive been able to do 1280x960 at 70hz, now i cant even get to 1280x960 at ANY refresh rate!!

ive already done "sudo dpkg-reconfigure xserver-xorg"

ive tweaked my setup only to include that resolition and ONLY my default bitdepth (24). still offers weird configurations (1184x8XX) or something like that instead.

right now im at 1280x1024 @ 60hz, but its killing me.......i need the 70+ HZ

the screen is a 17 inch viewsonic e70f+

thanks

---

### Post by Ianman on 2007-04-21
I am using the open source drivers with AIGLX and Beryl and I can go no higher than 1024x768 :(

btw, I have a Radeon X850XT PE

---

### Post by Ianman on 2007-04-21
I found a solution for my situation. Seems I needed to manually set the Horizontal and Verticle refresh rates of my monitor in the xorg.conf file. This is what mine looks like now:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	#HorizSync	28-51
	HorizSync	30-81
	VertRefresh	56-75
EndSection

I just googled on the technical specification for my monitor and entered those values. If you have your use manual it may also be in there!

Hope this helps.

---

### Post by eldragon on 2007-04-22
i got tired of waiting for ati......

now im using the OS drivers, where everything works as advertised......

---

### Post by petaskeeta on 2007-05-12
I'm having the same problem trying to achieve the same resolution. I am stuck at 1024x768 but I'm at a 85Hz refresh. I'm trying to run 1280x960 at any refresh. 

Here is my setup:

Feisty amd64
ATI - Radeon 9800 using fglrx drivers from restricted package

---

