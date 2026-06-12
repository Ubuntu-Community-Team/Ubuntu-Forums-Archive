---
title: "need help to fix mbr without windows cd"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by helltone on 2007-03-23
Hello all,

I had kubuntu installed on my laptop, but I'll give it to my sister (I got a new one yeah \o/) and therefore I wanted to uninstall it and use the "recovery partition" that came with it. This partition contain some sort of norton ghost that copies to the second partition an image of windows home + drivers.

So first I used qparted to repartition my disk hda into three partitions exactly as it was before installing kubuntu (the first one contains the factory recovery data):

hda1 recovery fat32 ~3gb made bootable for recovery
hda2 windows fat32 ~30gb
hda3 data fat32 ~27gb

then I rebooted and followed the recovery procedure, everything went very well but... when I rebooted again I got:

Grub loading stage 1.5.

Grub loading, please wait...
Error 17

Ops, I broke mbr/grub... I searched a lot and found out that I could try "fdisk /mbr" using windows CD recovery mode or something like that, but the thing is: I don't have a windows CD!!

However, I do have kubuntu's DVD. Is it possible to fix this problem without windows CD? (step by step would be much appreciated!!)

Thanks a lot!
Helltone

---

### Post by veloce on 2007-03-23
Why not re-install (k)ubuntu and give it to your sister like that?  Don't feed the problem!

---

### Post by anaconda on 2007-03-23
fdisk /mbr 
works also from old msdos floppies.. eg. win98 recovery floppy can be found from friends or the net quite easily.. or borrow someone elses windows CD to fix the mbr..

freedos would propably work too..

and if you dont have a floppy -drive you can meke a CD bootable using the floppy image.. (eg in k3b or nero) and then you can boot the floppy image from a CD and type fdisk /mbr..

one option is to install lilo to the mbr. it can boot windows too. and because it is (unlike grub) completely in mbr it doesn't need any files from other partititons..

or install some other windows compatible bootloader

just a few thoughts..

---

### Post by Bachstelze on 2007-03-23
Since you seem to own a Win XP license for that computer, is it absolutely your right to make a copy of a CD for yourself, for example after borrowing it from a friend. That's what I would do if I were you, they stil can be useful sometimes :p

---

### Post by civilmonkey on 2007-03-23
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) is free (or donation) bootable cd with lots of utilities.  Read a bit on the site, but i'm pretty sure one of the partition utilities has a fix mbr option.  Worked for me.

---

### Post by muzzamo on 2007-05-19
So windows fdisk /mbr is safe to use and wont break grub?

What exactly does it do? How can it know to setup grub and ubuntu properly when it doesn't even know what it is?

---

### Post by BHelts on 2007-05-19
fdisk /mbr or FIXMBR does not fix the mbr with grub.  it repairs the mbr to it's native state without grub.

---

