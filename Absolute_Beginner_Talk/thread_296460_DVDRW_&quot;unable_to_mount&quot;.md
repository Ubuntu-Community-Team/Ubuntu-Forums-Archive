---
title: "DVDRW &quot;unable to mount&quot;"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by drx0 on 2006-11-09
I installed Edgy using an EIDE DVDRW drive but I can't mount a CD.   It says, "unable to mount" at the GUI mounter and at the command line mount.  I put a Windows hard drive in and it works fine.  I also tried a different brand & model of DVDRW and it doesn't work in Edgy either.  I tried commercial CDs, data CDs written on a Windows PC, music CDs, etc.  Please help -- I'm stuck!

---

### Post by Ecthelion on 2006-11-10
You probably have the same problem as in [this thread]("http://ubuntuforums.org/showthread.php?t=295308")...

This is a problem wich should have a solution since you used a cd to install ubuntu in the first place...

So:

Do you find your cd drive in /etc/fstab ?
DO you find your device in the list you get after doing
```
hal-device-manager
```
?

---

### Post by Radiera on 2006-11-10
This happened because of the new idiotic fstab lines.
in your console type sudo nano /etc/fstab.
Modify the cd-rom line so it will look like that:
/dev/hdc        /media/cdrom0   auto user,noauto     0       0

---

