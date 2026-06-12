---
title: "Can not install Ubuntu on whole hard drive"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2007-12-03
Hi, this issue has happened on two different computers...so I guess it isn't just a glitch and was wondering if anyone knew the solution to this problem.

A partition was made so both Windows and Ubuntu can be on the hard drive.
At a later time the owner of the computer decided to write over the Windows partition and reinstall Ubuntu on the whole drive.
When trying to install over the whole drive with the Live CD, you get errors saying the partition editor failed.
If one uses the alternate (textual) install disc, one is able to write over the whole disc without any issues.

Does anyone know how to make Ubuntu write over the whole hard drive with the Live CD? This happened once with a Ubuntu 7.10 disc on a Gateway laptop and once with a Xubuntu 7.10 disc on a Dell desktop. Thanks!

---

### Post by kelbizzle on 2007-12-03
Try formatting with a gparted live cd first. [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by kevindubrow on 2007-12-04
That sounds good; I'll probably end up doing that. But is there just a command I could run through the terminal that would partition the drive?

---

### Post by kelbizzle on 2007-12-04
Yes. Although I've only had to do it once. It's do-able this is where I got my info. [http://linux.about.com/od/ptn_howto/a/hwtptn06t00.htm](http://linux.about.com/od/ptn_howto/a/hwtptn06t00.htm)

---

### Post by kevindubrow on 2007-12-04
So if I just told it to delete all of the partitions, everything should work out?

---

### Post by jaybombalous on 2007-12-04
windows will make no difference to the LIVE CD, formatting and editing the partitions is OS independent. I know because I installed ubuntu over top of windows xp with no problems.

I hate when I hear people say things like u have suggested, it really makes no difference.

---

### Post by kevindubrow on 2007-12-04
I'm confused, what makes no difference? I'm sure deleting the partitions manually so I can write on the hard drive will make a difference since the Ubuntu installer is having issues.

---

### Post by kelbizzle on 2007-12-04
yea just try formatting it with fdisk first. You'll be fine.

---

### Post by kevindubrow on 2007-12-04
Thank you very much!

---

### Post by kelbizzle on 2007-12-04
no problem.

---

