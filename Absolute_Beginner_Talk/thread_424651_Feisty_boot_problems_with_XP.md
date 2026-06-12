---
title: "Feisty boot problems with XP"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Fishmoney on 2007-04-26
Before I installed Ubuntu I had one hard drive with two partitions: one small partition for 32bit windows XP and the rest for 64bit windows XP.  I installed Ubuntu (Feisty Fawn) and told the partitioner to make a new 15 gigabyte partition out of free space on the drive.
After installing, when I booted up I wasn't given the option of choosing either version of Windows that I had installed, so I went into /boot/grub/menu.lst and added this at the end:

title Windows XP
rootnoverify (hd0,0)
makeactive
chainloader  +1

when I choose windows as I boot up, I get this:

"Error 13: Invalid or unsupported executable format."

I know that Windows is still there, because I can see the files on the hard drive.  Could somebody help me out?

---

### Post by Jazztux on 2007-04-27
Hi,
can you post here the content of your /boot/grub/menu.lst file? We'll try to make it run... ;)

---

