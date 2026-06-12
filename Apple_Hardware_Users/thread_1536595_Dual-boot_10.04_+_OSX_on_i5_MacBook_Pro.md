---
title: "Dual-boot 10.04 + OSX on i5 MacBook Pro"
date: 2010-07-22
forum: Apple Hardware Users
---

### Post by calum on 2010-07-22
So, I've run into the same problem as many other people in the past... have installed rEFIt, and Ubuntu 10.04, but it won't boot... when I select Linux from the rEFIt menu, it just goes straight to black screen, flashing cursor.

Have tried multiple different ways of partitioning (with BootCamp, with gParted) and installing (with/without swap partition, with/without separate boot partition), and even three completely different Linux distros (OpenSuSE 13, Fedora 11), all with the same result, so I'm beginning to wonder if it's even possible on an i5 MBP.

Thing is, I could live with things for now if there was even just a way of booting into my Ubuntu install via the install CD (perhaps via the 'rescue a broken system' menu item?), but I can't even figure out how to do that. Is it possible? 

Closest I've managed so far is to mount the root directory (/dev/sda3) in rescue mode and run 'startx', but that gives a far from properly-functional desktop...

---

### Post by sircram on 2010-11-24
[I'm having the same issue...]("http://ubuntuforums.org/showthread.php?p=10159485#post10159485") Let me know if you get a response.

---

### Post by calum on 2010-11-24
I eventually got it working, using 10.10 instead of 10.04.  As far as I'm aware, I did nothing else different, and even now, it sometimes hangs before it gets to the GRUB menu.  But nine times out of ten, it works.

---

### Post by jsiples on 2010-11-24
Did you do anything special to boot the install disk?  I cannot get it to boot my install disk, it won't detect it at all.  Nor will it detect a USB flash drive :-/  Both work fine when I get into OS X though, so its not hardware related from what I can tell.

---

