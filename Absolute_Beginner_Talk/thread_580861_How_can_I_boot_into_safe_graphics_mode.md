---
title: "How can I boot into safe graphics mode?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Warpnow on 2007-10-19
I first booted the live cd and it had to be in safe graphics mode, but the install was not working, so I used the alternate cd, except I didn't see anywhere to set safe graphics mode in that. 

I installed Xubuntu, but once the xubuntu loading bar is gone, the monitor no longer detects a signal. I tried 2 different video cards.

I am currently running a live cd of DSL. Could someone tell me how I can force it to boot in safe graphics mode?

---

### Post by kshane on 2007-10-19
Post your question in this forum.  You're more likely to get an answer...

Ubuntu Forums > The Ubuntu Forum Community  > Main Support Categories > Multimedia & Video

Kevin

---

### Post by Warpnow on 2007-10-19
I just installed via the alternate cd and it doesn't seem my graphics drivers are working at all. Bios loads, as does the Xubuntu loading screen...then, nothing. Monitor loses signal.

I can boot the live cd if I user the safe graphics mode...is there a way to do that for the actual install? A boot parameter or something?

---

### Post by bigken on 2007-10-19
you should be able to select safe mode from the grub menu

---

### Post by Warpnow on 2007-10-19
> **bigken said:**
> you should be able to select safe mode from the grub menu

Yeah, but its a command line interface, and I don't know what to do from there to get my graphics working.

---

### Post by Warpnow on 2007-10-19
What I need to know is how I can, from the command line, reset my graphics drivers to something basic and simple, like those in the safe graphics mode...so it will boot.

Anyone know?

---

### Post by bigken on 2007-10-19
sudo dpkg-reconfigure xserver-xorg

---

### Post by bigken on 2007-10-19
what type of graphics card do you have ?

---

### Post by gubemton on 2007-10-27
I have a similar problem: Ubuntu doesn't care what video card I have when booting from the CD in "safe graphics mode". However, following installation the display is screwed (like a  normal live CD boot--hence my taking the "safe graphics option) and I have no idea what to tell the xorg configuration thing; I just want it to work *after* installation the same as it did *before*! (Oh, and in case it matters, the video card is an S3 Savage4). 

A useful tweak for the CD would be an "install to boot in safe graphics mode" option under  "installation".

---

