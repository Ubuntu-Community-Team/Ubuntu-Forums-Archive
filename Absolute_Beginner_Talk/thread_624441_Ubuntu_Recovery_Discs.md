---
title: "Ubuntu Recovery Discs"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Elitegunslinger on 2007-11-26
Kind of a simple question.

Is there anything that I could create recovery discs for ubuntu with?  I would really just like to burn a dvd and have all the drivers ready to go for a reinstall.  Is there anyway to do this?

---

### Post by torgrot on 2007-11-27
partimage will make a copy of a partition on another drive i.e. a dvd writer.

torgrot

---

### Post by mikewhatever on 2007-11-27
> **Elitegunslinger said:**
> Kind of a simple question.

Is there anything that I could create recovery discs for ubuntu with?  I would really just like to burn a dvd and have all the drivers ready to go for a reinstall.  Is there anyway to do this?

There are several tools you can ttry
[http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)
[http://psychocats.net/ubuntu/partimage](http://psychocats.net/ubuntu/partimage)

---

### Post by rzrgenesys187 on 2007-11-27
Thanks for the info.  A buddy of mine at school and I were talking about this the other day, very convenient this thread was posted.

---

### Post by Threbus5 on 2007-11-27
Think about this -

Instead of a "recovery disk" , keep a current tar of the hard drive in a directory on the hard drive (remember to exclude such things as mnt, media, sys, lost+found, and proc.)
If the system corrupts, restore from the tar.

Or

Keep a current tar of the hard drive on an external drive or pen drive (remember to exclude such things as mnt, media, sys, lost+found, and proc.).
If the system corrupts, reinstall from the original system disk and then restore from the external tar.

Good luck

---

### Post by Elitegunslinger on 2007-11-27
Thanks for the quick reply, I just hate reconfiguring things all the time so I figure its better to have a back up.

---

