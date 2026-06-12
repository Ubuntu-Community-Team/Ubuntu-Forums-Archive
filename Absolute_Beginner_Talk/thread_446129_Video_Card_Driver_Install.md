---
title: "Video Card Driver Install"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by aaron_summer on 2007-05-16
I am so new to Ubuntu (and Linux) that it is not funny.

Yesturday I installed Ubuntu Server and ran apt-get install kubuntu-desktop (I need the GUI), and noticed the slow performance of my video card.

It appears as KDE (or X Server) has detected it as a generic VESA card.

I have a S3 Integrated Videocard (I think it is a VIA Unichrome) and selected the card and set the allocated memory for it in the KDE video settings. The whole thing crashed on me.

The vendor (ASUS) has linux drivers for this card but does not include any directions. Should I install the driver for better performance or leave the default and suffer through the slow GUI?

---

### Post by duan on 2007-05-16
Good luck!
I run a via epia fanless box with the latest xubuntu, it ran ubuntu before.

I've tried, and tried and the best thing for the via unichrome is ubuntu's "via" driver which should be installed by default. Ununtu was one of the only heroes to include a driver for via. 

edit: i should of read your post better. Ubuntu has a driver in the repositories, it is called "via", you can look for it in synaptic. the via driver works nicely, but the unichrome chipset is rubbish. It is intended as a 2D display driver for automotive use with mpeg acceleration. i.e. a dvd player in a car.

I saved myself loads of hassels when I read that the unichrome chipset DOES NOT SUPPORT OPENGL. It does a fair few of the instructions that microsoft's direct-X uses but not all of it so It crashes windows games quickly.

I'm not too savvy debugging X drivers but if you scan your /etc/X11/xorg.conf file you will see a section for the video driver like this:
Section "Device"
        Identifier      "VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics"
        Driver          "via"
        BusID           "PCI:1:0:0"
EndSection

vesa is the standard which is definately not what you want. the via is at least loads better than the plain vanilla vesa driver.

if yours doesn't say via start synaptic (either from menu or terminal( type in "sudo synaptic") ) and search for and install:
xserver-xorg-video-via

the unichrome is not good but it certainly never ever crashed while running the desktop (even with some eye candy). never ever, for 80 days straight before I moved house and had to reboot.

Nothing you can do to it will make all the flashy bits from KDE/gnome run nice, especially the 3D stuff forget the compiz/beryl candy.

Honestly the few composite effects like transparancy that XUBUNTU (xfce-desktop) does are the most I get out of it, and it does so decently.

Having said that this via fanless mobo ran ubuntu so nice after I recompiled the kernel especially for the via processor (frequency scaling came up) i love the machine.
I had to recompile with a very new kernel since some other nice kernel developer integrated support for the numerous thermal sensors bitties so I could check how hot the fanless thing was getting)

The via video hardware is just not nice, especially blurry on an lcd. it might be better on your asus if they bothered to solder a few more capacitors onto the motherboard.

Anycase I use it as a low power always on machine to backup several others and email and browsing- which I access through vnc from another machine with a nice graphics card. So i leave the machine on, running email etc and it never crashes.

---

