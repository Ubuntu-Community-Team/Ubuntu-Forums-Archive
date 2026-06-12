---
title: "How do i unpartition a hard drive"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by firstblood on 2006-11-28
I would like to know how to unpartition my hard drive
so i can reinstall ubuntu and use it as my operating system.

---

### Post by nickburns on 2006-11-28
If you are going to completely ditch everything on the HD, then I  would boot the live CD and do a fresh install.  During the install you can select to format the entire drive.

---

### Post by firstblood on 2006-11-28
thank you nickburns....now another question. how do i 
unpartition the hard drive and leave windows xp on 
without formatting the whole hard drive if i put it on
another pc as well ?

---

### Post by nickburns on 2006-11-28
So we all understand, you have Windows on a pc, and you want to dual boot?  For example you want the option to boot windows or ubuntu?  If so are they on different hard drives? or the same HD?

---

### Post by firstblood on 2006-11-29
ok , i know i'm a dummy and i apologise for
asking a silly question.

but yes. i have both systems on the same hard drive
and how do i remove ubuntu and restore my pc back with 
windows xp as the operating system with the hard drive not partitioned.

---

### Post by freshofftheufo on 2006-11-29
You'd have to use something that can resize partitions, such as gparted ([http://gparted.sourceforge.net/)](http://gparted.sourceforge.net/)). Use the gparted LiveCD so that you can edit your partitions without any OS running, and just delete the Ubuntu partition. Then you'd just resize the XP partition back to full size.

If you don't want to bother with all that, just format the second partition in Windows and use it as it is.

---

