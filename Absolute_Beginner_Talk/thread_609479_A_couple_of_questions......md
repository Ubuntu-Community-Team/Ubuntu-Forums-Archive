---
title: "A couple of questions....."
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by ntowakbh on 2007-11-11
Okay, I am pretty much new to Ubuntu, and Linux in general, so please forgive me if I ask "stupid" questions.

First thing is that I see my hard drive partitions on my desktop, what if I don't want them there? answered

What does it mean, for something to be "mounted," and what if I were to unmount a partition on my desktop? answered 

[EDIT]: Okay, I have a five button mouse, on my WindowsXP, hitting the far left makes me go back a page, hitting the far right button makes me go forward a webpage in a web browser....how could I make it do this on Ubuntu?

---

### Post by matthewcraig on 2007-11-11
You can run Ubuntu on just one data partition, with one for swap.  It's recommended to have a separate "swap" partition, though.  And mounted?  The easiest way to think of mounted is your CD-ROM drive.  When a disk is inserted and visible on your computer, it is mounted.  You are unable to remove a mounted disk, because it is in use.  Once you unmount the disk, then you can remove the CD-ROM and put a different one inside.  Mounting a hard drive works in much the same way.

---

### Post by forestpixie on 2007-11-11
if you don't want to see them on your desktop

Alt-F2 and type gconf-editor in the box, run

apps > nautilus - untick volumes visible shoul do it for you

---

### Post by ntowakbh on 2007-11-11
Loads of thanks to the both of you!

---

### Post by osxcapades on 2007-11-11
> **ntowakbh said:**
> What does it mean, for something to be "mounted," and what if I were to unmount a partition on my desktop?

Mounting a filesystem makes it readable (and also writable in many cases). You may be able to guess that if you unmount a filesystem, you can no longer read it or access it. Unmounting a device is usually needed to remove it AFAIK (if you intend to avoid problems).

---

### Post by ntowakbh on 2007-11-11
Okay, I have a five button mouse, on my WindowsXP, hitting the far left makes me go back a page, hitting the far right button makes me go forward a webpage in a web browser....how could I make it do this on Ubuntu?

---

