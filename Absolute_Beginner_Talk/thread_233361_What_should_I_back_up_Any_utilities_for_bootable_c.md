---
title: "What should I back up? Any utilities for bootable clones?"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Carbonfish on 2006-08-10
Hi all,

Sort of a n00b issue I guess, but are there any Linux utilities for making a bootable clone of my HDD in my IBM ThinkPad where Ubuntu lives? If not, what should I be backing up, and how easy (or difficult) is is to migrate back and forth to an external drive?

I have a 250 GB external drive that I use for storage and to back up my iBook. I use Carbon Copy Cloner to make a bootable clone of the internal drive of the Mac, and that works great. The problem here of course, is that CCC will only clone to a HFS+ formatted partition. I realize that one partition doesn't care what's on the other ones, so I have re-partitioned approx. 100 GB on the external drive as "free space". That said, I can format it as anything I like, and just need to get some guidance about how best to proceed.

If there is no reliable "cloning" utility available for Ubuntu, which directories should I copy to the external drive, and if I want to restore or recover, can I just paste them over the existing directories and "overwrite" them, or will that not work with this OS?

Thanks in advance for your patience with my n00biness.

KC

---

### Post by bscbrit on 2006-08-10
> **Carbonfish said:**
> Hi all,

Sort of a n00b issue I guess, but are there any Linux utilities for making a bootable clone of my HDD in my IBM ThinkPad where Ubuntu lives? If not, what should I be backing up, and how easy (or difficult) is is to migrate back and forth to an external drive?

I have a 250 GB external drive that I use for storage and to back up my iBook. I use Carbon Copy Cloner to make a bootable clone of the internal drive of the Mac, and that works great. The problem here of course, is that CCC will only clone to a HFS+ formatted partition. I realize that one partition doesn't care what's on the other ones, so I have re-partitioned approx. 100 GB on the external drive as "free space". That said, I can format it as anything I like, and just need to get some guidance about how best to proceed.

If there is no reliable "cloning" utility available for Ubuntu, which directories should I copy to the external drive, and if I want to restore or recover, can I just paste them over the existing directories and "overwrite" them, or will that not work with this OS?

Thanks in advance for your patience with my n00biness.

KC


[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by Carbonfish on 2006-08-10
Thanks for the link bscbrit. I will read and learn (I hope).

KC

---

### Post by aysiu on 2006-08-10
It's not bootable, but for cloning, you can try PartImage:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

For backups, I usually do something like this (I have a script for this set up on my Ubuntu desktop and my wife's Mac Powerbook): ```
rsync -av /home/username /media/backup
```

---

### Post by seshomaru samma on 2006-08-10
Aysiu , you say the partimage method is not bootable so ,lets say I copy my harddrive with partimage to another machine (with the exact same hardware), how can I make it boot?

---

### Post by aysiu on 2006-08-10
By "not bootable," I mean that if you copy it to a series of CDs or to a DVD, you can't just pop the CD in and have it restore your image automatically.

If you copy the image to a new hard drive, the hard drive should boot.

---

### Post by Carbonfish on 2006-08-11
Thanks aysiu, I'll check it out.

Kent

---

