---
title: "EAGLE Crashing X-server"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Zelandeth on 2008-04-05
Forgive me if this is a really simple fix - this is my first foray into the world of Linux since a brief (very confusing!) encounter with Red Hat back in 1999.

I was very happy to discover Eagle being available for Ubuntu, this is a great package which I've used since starting university.  Installation caused a few issues (from the Synaptic package manager) as it seemed to fail to set some necessary permissions, and didn't bother to give me a launcher for it - I managed to sort that out though.

What I don't seem to be able to sort out is that as soon as I start a new schematic and click on "add component" there are a few seconds of harddisk thrashing, then I get a brief burst of (quite pretty actually) multicoloured vertical lines on the display, before getting booted out to the login screen - I'm assuming that Eagle's doing something that's taking down the server though I could be well wrong.

The PC in question is rather archeic, but otherwise did work with Ubuntu straight out of the box.  It's an old Packard Bell iMedia, 1GHz Celeron, i810GL onboard graphics, 256Mb RAM (which I tried to upgrade to 1Gb last weekend before discovering the mobo only supports up to 512Mb...grrr...).

I'm guessing that there may be a log file somewhere which could at least tell me (and the more experienced of you out there) what's going on to see if there's anything that can be done to sort it out.  I'm looking suspiciously at the graphics subsystem at the moment, but could be wrong.

---

### Post by riven0 on 2008-04-05
This is most likely caused by having a video card driver that doesn't support direct rendering. If you have one of those old on-board graphics cards, you may be out of luck. In either case, you can list your graphics card type, or find out your model by typing: **sudo lspci** in the terminal.

---

