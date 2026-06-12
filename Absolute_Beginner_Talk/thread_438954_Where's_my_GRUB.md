---
title: "Where's my GRUB?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by shayshay on 2007-05-10
Hi everyone,

I'm trying to get Ubuntu 7.04 installed on an external USB drive.

I managed to get it to boot, where grub comes up and asks me to select what OS I want to boot from blah blah. And it boots into Ubuntu fine. I'm therefore assuming the GRUB was installed to the external drive as the only devices set to boot in the BIOS were the CD-ROM (position 1) and the external drive (position), with the internal drive excluded.

However, if I changed the BIOS settings so that the boot order goes:

1. CD-ROM
2. USB External Drive
3. Floppy
4. Internal Hard Disk

It boots straight into Vista using the internal drive.

I'm slightly confused therefore as to where the GRUB boot loader was installed and why it goes straight into Vista even though the USB external drive is above it in the boot order.

I've enabled boot from USB in the BIOS. I've done all that editing and recompiling of files to ensure that USB connectivity (loads modules, slows down time, lol). I'm sure when installing Ubuntu I told the installer to load GRUB onto (hd1, 0) or whatever the external drive was at the time...

Well. Can anyone point out where I went wrong? Or give me a soulution to how I can achieve:

1. When the USB drive is plugged in, it boots to Ubunutu.

2. Otherwise, it goes into Vista.

Many thanks,

:-({|= 

Shay

---

### Post by drowner on 2007-05-10
Stupid Question #1: You didnt have a vista cd in at the time?

---

### Post by shayshay on 2007-05-10
Nope! I don't even have a Vista CD...

:mad:

---

### Post by gohanssjn on 2007-05-10
It sounds to me like it installed GRUB to sdb1/hdb1 and gave it the "BOOT" flag.  When the drive is plugged in, it sees that flag and boots from it.  Wehn not plugged in, it boots the first partition it sees, namely Vista.

I know there is a way to move it, but I have never done that before.  i would search here for "move grub".

Also, I would download GParted and move the boot flag to Vista once you get GRUB installed, as Vista seems to not hibernate without that flag assigned to its partition.

Good luck!

---

