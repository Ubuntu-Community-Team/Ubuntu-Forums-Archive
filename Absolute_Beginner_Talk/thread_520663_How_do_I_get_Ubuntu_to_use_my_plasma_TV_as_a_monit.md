---
title: "How do I get Ubuntu to use my plasma TV as a monitor?"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by SanjoEel on 2007-08-08
Hi Folks. I know this might seem like a dumb question, but how do I connect my computer to my plasma screen tv? I am running Feisty, and I would like to use my tv as the monitor. It seemed pretty straightforward.  I tried connecting with a vga/s-vid adapter and after rebooting no joy, just a blank screen. I tried Vid1 & 2, etc.
 I don't even know if it is a good idea to use a plasma screen as a monitor? If someone could get me started with some thoughts on this I would appreciate it.

---

### Post by oilchangeguy on 2007-08-08
i'm gonna take a wild guess, and say your video card doesn't even come close to the resolution needed to make it work.

---

### Post by myoungf1 on 2007-08-08
Check you tv's owners guide to see what the resolution for the vga port is.  Mine is 1024x768.  You need to change your resolution to the specified resolution first before you plug it into the tv.

---

### Post by Hospadar on 2007-08-08
> **oilchangeguy said:**
> i'm gonna take a wild guess, and say your video card doesn't even come close to the resolution needed to make it work.

This shouldn't be a problem, only recently are good hi-def displays reaching monitor-like resolutions. (a regular tv has barely more resolution than my zen vision)

You might need to look into you X server settings to make sure it is outputting to the tv-out on your video card (obviosly that is not the case at the moment)

Have you installed the proprietary video drivers for your card (if the exist).  I know for nvidia cards at least the proprietary drivers offer a lot more features.

If you have an nvidia card, check [this]("http://sourceforge.net/projects/nv-tv-out") out.

After looking a little more, it looks like some things may need to be added to the xorg.conf file located at /etc/X11/xorg.conf, have a look at [this]("http://gentoo-wiki.com/TV-Out_with_GeForce#Adjusting") and the section just above it (ignore the installations on this page, they are for gentoo)

---

### Post by SanjoEel on 2007-08-08
Thanks for the suggestions, I'll do a little research and be back later.

---

### Post by bwtranch on 2007-08-08
You might be interested in Myth TV. I know that's not what you are asking about. I just thought you might like playing around with it.

---

### Post by SanjoEel on 2007-08-08
After some more googling I don't think that using the plasma tv for a monitor is such a good idea. It seems they like to burn.

---

