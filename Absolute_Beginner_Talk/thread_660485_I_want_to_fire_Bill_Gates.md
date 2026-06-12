---
title: "I want to fire Bill Gates"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by tripss734 on 2008-01-06
What is the best way to remove windows xp from a dual boot setup?

---

### Post by PurposeOfReason on 2008-01-06
Open up gparted on the live CD and delete it, then extend your linux partition to take up the full HDD.

---

### Post by icechen1 on 2008-01-06
Do a reinstall,choosing to take all the hard disk space,this is the safest one.

---

### Post by p_quarles on 2008-01-06
> **PurposeOfReason said:**
> Open up gparted on the live CD and delete it, then extend your linux partition to take up the full HDD.
After doing that, one would need to reinstall the bootloader. If it suddenly finds Windows missing, you'll get a nasty error. Here's how:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

> **icechen1 said:**
> Do a reinstall,choosing to take all the hard disk space,this is the safest one.
That's no more or less "safe" than anything else, and it's completely unnecessary.

---

### Post by mdpalow on 2008-01-06
> **p_quarles said:**
> After doing that, one would need to reinstall the bootloader. If it suddenly finds Windows missing, you'll get a nasty error. Here's how:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)


That's no more or less "safe" than anything else, and it's completely unnecessary.

agreed...

---

### Post by HermanAB on 2008-01-06
Hmm, I don't think you can extend a partition 'backwards'.  (Windows is most likely the first partition).

The easiest way is to simply keep the windoze partition as NTFS, mount it in Linux and erase everything on it.  NTFS is a perfectly good and robust file system, so there is no reason why not to use it as is. 

Cheers,

Herman

---

### Post by PurposeOfReason on 2008-01-06
> **HermanAB said:**
> Hmm, I don't think you can extend a partition 'backwards'.  (Windows is most likely the first partition).

The easiest way is to simply keep the windoze partition as NTFS, mount it in Linux and erase everything on it.  NTFS is a perfectly good and robust file system, so there is no reason why not to use it as is. 

Cheers,

Herman
Oh, you can, but it is a right pain. I'll extend it to the left, as it's called, and then move everything in small chunks. I had a 10GB installation on a 150GB partition (it was storage) and did that without realizing it. 28 hours later. . . yeah. It was a fast HDD too.

---

### Post by thelatinist on 2008-01-07
> **PurposeOfReason said:**
> Oh, you can, but it is a right pain. I'll extend it to the left, as it's called, and then move everything in small chunks. I had a 10GB installation on a 150GB partition (it was storage) and did that without realizing it. 28 hours later. . . yeah. It was a fast HDD too.

Agreed.  I did this when I deleted my Windows partition.  It took 14 hours.

If I were going to do it again I would create a new partition at the beginning of the drive, mount it somewhere like /media/new_partition, and pipe everything important in root to the new partition using tar:

```
cd /
sudo tar cf - --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/media --exclude=/sys  * | ( cd /media/new_partition; tar xfp -)
cd /media/new_partition
sudo mkdir proc lost+found mnt media sys 
```

Actually, this is exactly what I did when I wanted to create a testing system I didn't mind breaking, and it worked like a charm.

---

