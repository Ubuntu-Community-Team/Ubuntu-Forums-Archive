---
title: "Dual Boot"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by MasterAlone on 2008-01-03
Sounds silly but I'm using the LiveCD to test and am considering installing Ubuntu but I would like to know if a) a dual boot is created during installation and b) can I install to a D: drive?

TIA

---

### Post by Fleece Flamingo on 2008-01-03
I can answer question the first. Yes it is created upon installation. As for the second question, I am not sure. You can install two different os' on two different HDD if thats what your asking.

---

### Post by MasterAlone on 2008-01-04
Thank you, that's what I was asking, wasn't sure if I was going to have to partition My C: drive.

---

### Post by jordank on 2008-01-04
In ubuntu, there's no such thing as a "d:" per se.  You can have two operating systems on a hard drive, however, you need to have a partition.  To do this, there are a bunch of steps you should follow online before going ahead and making a linux partition.  For example:  if you are currently using a window box, you will want to clean it up before attempting to install. Windows is very messy, and leaves traces of programs and files all over your harddrive.  You will want to do a disk defragmentation before attempting to install.

However, when you are ready to install, click the install button on your live cd (should be on the desktop) and you will go through a wizard.  This wizard can create partition for you, so you can do exactly what you're trying to do.  You will select the option "use largest free space" and the ubuntu partition will take up that part of your harddrive.  Or you can manually go through the installation and alot a certain amount of space for ubuntu, and keep some for windows if you choose.  It's very dynamic, post again with further questions.

---

### Post by MasterAlone on 2008-01-04
So if I have Windows XP on my C: drive and want Ubuntu to install to the D: drive, it can't be done?

---

### Post by mikewhatever on 2008-01-04
> **MasterAlone said:**
> Sounds silly but I'm using the LiveCD to test and am considering installing Ubuntu but I would like to know if a) a dual boot is created during installation and b) can I install to a D: drive?

TIA

1. Not necessarily. It is possible to install Ubuntu by itself, letting it format the entire drive, or aside another operating system. You have to know what to do. Please review this guide first [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing).

2. Yes. D:\ is just a convention used in Windows. Ubuntu can be installed to first and none first or logical and primary partitions.

> So if I have Windows XP on my C: drive and want Ubuntu to install to the D: drive, it can't be done?

Yes it can. To settle it, you can install Ubuntu on any drive, from C to Z.

---

