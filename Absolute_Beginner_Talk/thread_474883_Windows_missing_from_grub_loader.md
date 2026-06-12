---
title: "Windows missing from grub loader?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-06-15
I use Ubuntu almost all the time but some while ago windows disappeared from my grub loader. I have tried the Super Grub Disk which can't seem to restore my option to boot windows XP. The hdd1 is still complete and contains windows, is it possible for me to perform this miracle and get the option to boot it again. Although i could manage without windows my canon printer gives better results with xp and the canon drivers (unfortunately).

---

### Post by andymushu on 2007-06-15
in terminal, type "sudo gedit /boot/grub/menu.lst" that should open up your grub configuration file. at the bottom there should be a list of the things that it shows on the grub, like "ubuntu kernel..." etc. simply add the following text somewhere within there and you should see xp on your grub.

title Windows XP
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

if you have two hard drives with xp on one and ubuntu on another, just add "root (hd1,0)" as the second line. if it launches into recovery mode for xp, change that line to "root (hd1,1)". make sure if youa re booting form two hard drives to set the ubuntu drive as master.

---

