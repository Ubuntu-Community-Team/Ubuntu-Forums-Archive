---
title: "external hard drive plight (need to boot twice in windows - but i have no windows)"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by pxxxner on 2007-06-14
what is the alternate solution to the boot twice in windows in order to run chkdsk on a corrupted external hard drive when one no longer has windows?

---

### Post by BHelts on 2007-06-14
you can go to [bootdisk]("http://bootdisk.com").com and download dos6.22 and boot into it.  it has chkdsk.exe on it and supports USB drives.

---

### Post by pxxxner on 2007-06-14
> **BHelts said:**
> you can go to [bootdisk]("http://bootdisk.com").com and download dos6.22 and boot into it.  it has chkdsk.exe on it and supports USB drives.

thanks.  i'll give it a try.

---

### Post by BHelts on 2007-06-14
not a problem, but i just thought of something.  the utility used to make the boot disk is a .exe.  you could try it in wine although i don't know if it would work or not as it looks specifically for the A: drive.  i'll look for another solution if that doesn't work for you.

---

### Post by BHelts on 2007-06-14
[Here]("http://s93616405.onlinehome.us/bootdisk/622c.zip") is a copy of dos6.22 with a program that is supposed to work in Linux, although to be honest i haven't tried it.  good luck.

---

### Post by pxxxner on 2007-06-14
> **BHelts said:**
> [Here]("http://s93616405.onlinehome.us/bootdisk/622c.zip") is a copy of dos6.22 with a program that is supposed to work in Linux, although to be honest i haven't tried it.  good luck.

yea, i have no a drive...i am working on a laptop...

---

### Post by pxxxner on 2007-06-14
> **BHelts said:**
> [Here]("http://s93616405.onlinehome.us/bootdisk/622c.zip") is a copy of dos6.22 with a program that is supposed to work in Linux, although to be honest i haven't tried it.  good luck.

i can't seem to extract the zip...i don't think the link was good.

---

### Post by pxxxner on 2007-06-14
a mirror (that works) for posterity:  [http://1gighost.net/virginia/622c.zip](http://1gighost.net/virginia/622c.zip)

---

### Post by pxxxner on 2007-06-14
man, i hate talking to myself.


i don't have a floppy drive so it would seem that this method is worthless.

---

### Post by BHelts on 2007-06-15
indeed.  sorry about that.  a floppy would be a necessity if one were to try to create a bootable floppy.
if you have your windows install disk, you can boot into the recovery console, i'm pretty sure chkdsk is there as well, although not positive.

[edit]  i just checked and yes, chkdsk is there.

---

### Post by pxxxner on 2007-06-16
if i still had my windows start up disk i would have used it already.  i talked with some linux gurus at work and they offered to help me out with ...company resources...hehe.  they are ubuntu wizards...so i should be alright.  thanks anyway.

---

