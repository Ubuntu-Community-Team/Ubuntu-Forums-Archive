---
title: "Ubuntu won't boot if Ghosted from other HDD?"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Crickster on 2007-03-11
Hi guys,

I've been using Ubuntu Dapper for a good few months now & my 40gb HDD is nearly full.
All I want to do is to Ghost the whole HDD over to an 80gb one (using a Norton Ghost floppy)

I tried this but the new 80gb drive won't boot. It gets to the stage where it says GRUB and then goes no further!!??

(The drive dual boots with Windows 2K - relevant?)
I tried booting from a Knoppix DVD to see if I could see if it was something to do with the menu.lst config but when I tried to access the partition it said the filesystem was unknown (although I could access the NTFS one OK).

I assume its either something to do with the MBR or the menu.lst but I have no idea how to fix it???
Thanks in advance.....

---

### Post by Jonam on 2007-03-11
I did something similar. I had a Win98 PC with a bad 30GB hard-disk (C: drive - master) which I wanted to run as dual boot with Ubuntu on a new 250GB drive. I installed the new drive as D: drive (slave) and copied Win98 across using a ghosting utility from Seagate. I then loaded Ubuntu onto a second partition on this new hard-drive. My system would happily boot off D: drive with Grub when I set my system BIOS to boot off the slave drive.

When I finally ditched the old drive and moved D: drive (slave) to the C: drive position (master), it failed to boot. Turns out that you have to do the following:

1) Re-install GRUB from the LiveCD (there is a tutorial in these forums I think)
2) Edit the menu.lst file (using LiveCD again) to show the correct hard-drive locations for booting from (eg hdb3 changed to hda3) and,
3) Fix up /etc/fstab to show correct locations of the drives

Also remember to adjust the PC BIOS to boot off the correct drive at startup. I have some notes somewhere on how I did this. If you can't figure it out, I can find them and provide more information.

Jonam

---

### Post by HereInOz on 2007-03-11
Ghost4Linux does a much better job of ghosting a Ubuntu system to another HDD.  It doesn't handle the partition re-sizing like Norton Ghost does, but after you ghost the disk, you just boot from a GParted CD and resize the partitions, and the thing will boot.

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

---

### Post by seshomaru samma on 2007-03-11
I used norton ghost to copy an installation of xubuntu to a number of similar boxes. in most of them i had to reinstall grub. if you have a gentoo system rescue CD - reinstalling grub is much faster 
basically it's :
```
grub
```
```
find /boot/grub/stage1
```
replace the question marks in the following command with the output of the last command:
```
root (hd?,?)
```
then
```
setup (hd0)
```
and
```
quit
```

---

### Post by linuxjerk on 2007-04-02
Some one needs to find a disk duplicator program so you don't have to reinstall grub.

---

### Post by linuxjerk on 2007-04-02
All those still require the disk be unmounted to copy. Try G4U I got it to work on my system.
You can either do floppies or cd.
[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

---

