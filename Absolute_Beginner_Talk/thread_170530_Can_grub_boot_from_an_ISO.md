---
title: "Can grub boot from an ISO"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by enopepsoo on 2006-05-04
I use qemu to boot some live cds (ISOs) but it is fantastically slow.  Rather than reformating my hard drive and whatnot, or the obvious "burn it to a cd" idea, I was just wondering if anyone has ever had any success with booting straight from an ISO file.

---

### Post by jason.b.c on 2006-05-04
[QUOTE=enopepsoo]I use qemu to boot some live cds (ISOs) but it is fantastically slow.  Rather than reformating my hard drive and whatnot, or the obvious "burn it to a cd" idea, I was just wondering if anyone has ever had any success with booting straight from an ISO file.[/QUOTE]


I'm not sure, but i don't think that can be done.  :-({|= 

I'm preaty sure the *.iso* **has to be** burn't on a disk as an image and thats the only other way you can boot it..

But then again, I don't know everything, so..???:-$

---

### Post by lha on 2006-05-05
Straight from iso - no, but from hd yes. I have booted Ubuntu live cd, Knoppix and DSL from hd a long time ago, so I do not remember everything I had to do to make it work.

I had a partition (you can probably use an existing partition) where I extracted the contents of a live cd. Then I copied kernel and ramdisk images that can be found somewhere on the cd to /boot. (In Ubuntu live this means files vmlinuz and initrd.gz found in /install.) Live cd's I tried use isolinux to load kernel. I looked into /isolinux/isolinux.cfg to find out the correct kernel options and finally added an entry to /boot/grub/menu.lst that booted the "live cd" from hd.

Take a look at [http://ubuntuforums.org/showthread.php?p=687306#post687306]("http://ubuntuforums.org/showthread.php?p=687306#post687306") . There's some info you might be interested in.

---

### Post by 3rdalbum on 2006-05-05
The latest version of QEMU supports a kind of virtualisation - have you tried that to see if it solves your speed problems?

---

### Post by Sef on 2006-05-05
Here's a wiki on the subject of installing via a hard drive.

[https://wiki.ubuntu.com/Installation/HardDriveAndPcmcia?highlight=%28Install%29]("https://wiki.ubuntu.com/Installation/HardDriveAndPcmcia?highlight=%28Install%29")

---

