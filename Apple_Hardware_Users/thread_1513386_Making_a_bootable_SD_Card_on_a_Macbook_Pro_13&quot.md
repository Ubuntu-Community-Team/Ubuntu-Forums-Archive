---
title: "Making a bootable SD Card on a Macbook Pro 13&quot;"
date: 2010-06-19
forum: Apple Hardware Users
---

### Post by palo.verde on 2010-06-19
Hi,

I'm trying to make a bootable SD card on my macbook pro with built in sd reader so that I can load ubuntu netbook on my eee pc.

I followed the instruction on the Ubuntu Netbook download page, and it appears to work, but the SD card isn't bootable.  I've tried to boot from it on both the eee pc and the macbook.

If you know how to do this, or know of some alternative way I can load ubuntu netbook on my eee pc that would be great.

Thanks for the help,
-Samuel

---

### Post by Jeroensum on 2010-06-20
Since I would be totally lost on a Mac system my first question is if you can boot a live CD on your Mac?

If so, boot it up, open up a terminal and run: sudo apt-get install unetbootin && unetbootin

A program should popup which should allow you choose a disc image to put on the sd-card and it will make your sd-card bootable.

---

