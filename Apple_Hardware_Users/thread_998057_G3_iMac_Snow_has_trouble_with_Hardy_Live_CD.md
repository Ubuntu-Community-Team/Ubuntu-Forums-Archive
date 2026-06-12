---
title: "G3 iMac Snow has trouble with Hardy Live CD"
date: 2008-11-30
forum: Apple Hardware Users
---

### Post by dai_vernon on 2008-11-30
I recovered a 700 MHz imac g3 snow and I'm trying to install hardy.  Loading the PowerPC live CD, I have gotten unsatisfactory results with the following choices:

live: computer powers down partway through load
live-powerpc: same as live
live-nosplash: successful, but drops to a command prompt and startx errors out (I'd prefer a gui)
live video=ofonly: perpetually hangs with a blinking cursor and no prompt

As far as I know the hardware is fine - what might the issue be?

---

### Post by dai_vernon on 2008-11-30
The startx error is:

Fatal Error: No displays found.

Does this mean that there are no drivers for my screen?  Where might I find them / get them / what distro might contain them?

---

### Post by stream303 on 2008-12-01
The drivers are there, although you may have to manually specify "r128" in your /etc/X11/xorg.conf :

[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3)

How much ram is in that machine?  I believe it originally came with 128mb, and that may not be enough to support the live-cd graphics requirement.

You may want to try the "alternate" text-based installer, which will at least get the system installed, and then later work on the manual reconfiguration to support your video...

---

### Post by dai_vernon on 2008-12-01
It has 256 megs of ram.  The alternate install is an option - when I get back home to play with it some more I'll try that and the xorg thing.

---

