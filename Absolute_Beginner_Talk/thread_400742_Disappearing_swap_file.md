---
title: "Disappearing swap file"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by RxRated on 2007-04-03
My swap file mounts fine when Ubuntu boots, but if I hibernate my computer, when it is restored my swap drive messed up.  I open GNOME partition editor and the drive is unformatted.  I re-format the drive to linux-swap, and turn swapon, and everything is good until I hibernate again.  I have 512 mb of ram and my swap file is 520mb.  I'm running Edgy.  Any ideas why hibernate wipes out the linux-swap format?

---

### Post by ComplexNumber on 2007-04-03
just curious, but how do you know that its unformatted?

---

### Post by dwblas on 2007-04-03
> I open GNOME partition editor and the drive is unformatted.It could also be that the partition editor does not report, or perhaps recognize the swap partition's type.  Try fdisk or cfdisk /dev/hdx.  Don't change anything though, as the partition is mounted.  Also, try swapon -s.  BTW, invoking swapon a second time will not hurt anything.  Swapon will skip any drive that is already active according to man swapon..

---

### Post by jakev383 on 2007-04-04
> **RxRated said:**
> My swap file mounts fine when Ubuntu boots, but if I hibernate my computer, when it is restored my swap drive messed up.  I open GNOME partition editor and the drive is unformatted.  I re-format the drive to linux-swap, and turn swapon, and everything is good until I hibernate again.  I have 512 mb of ram and my swap file is 520mb.  I'm running Edgy.  Any ideas why hibernate wipes out the linux-swap format?
This is not the first thread on this.... I have one here:
[http://ubuntuforums.org/showthread.php?t=400673](http://ubuntuforums.org/showthread.php?t=400673)
And I just posted in another thread that has the exact same issues..... If I find a fix I'll post again!

---

