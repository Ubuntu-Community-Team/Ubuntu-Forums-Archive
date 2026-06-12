---
title: "[SOLVED] Is it impossible to install Ubuntu if your harddrive has bad sectors?"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by spydon on 2007-08-23
I have tried to install Ubuntu on my girl friend computer but Is it impossible to install Ubuntu if your harddrive has bad sectors?

---

### Post by henriette_holm on 2007-08-23
Hmm, personally I wouldn't install any OS on a disk with bad sectors. Replace it with a new one - they don't cost much these days.

/Henriette

---

### Post by silent1643 on 2007-08-23
dude go buy a new hard drive - go for a cheap one 

if you dont care about bad sectors you must not care to have the best hard drive on earth, so go spend a little mula and buy a hard drive and also buy a piece of mind \\:D/

---

### Post by Xyphus on 2007-08-23
If you use a disc utility to mark the bad sectors first, you might be able to install.  I wouldn't recommend it however.  Bad sectors on a hard drive tend to multiply as the hard drive fails.  I would recommend just replacing the drive if at all possible.

If that is not an option however, most hard drives come with a utility on CD which will allow you to boot from the CD and prepare the drive.  I believe you might be able to do this from a LiveCD as well.  I'm not sure if fsck will mark bad sectors or not.  (I usually use utilities from something like Hiren's Boot CD to troubleshoot drives...)

---

### Post by spydon on 2007-08-23
Okay, thx for the answers :)
Il buy a new one

---

### Post by Paulmd on 2007-08-24
> **spydon said:**
> I have tried to install Ubuntu on my girl friend computer but Is it impossible to install Ubuntu if your harddrive has bad sectors?

Impossible: probably not. But  definitely a bad idea. According to a recent Google study on hard drive failures (involving 100,000 el-cheapo consumer grade hard drives that they owned), a hard drive with even 1 bad sector is 39 times more likely to fail within 6 months as one without. The more bad sectors, the more you're tempting fate.

One more thing: hard drives don't always die all at once, they can linger, in an ever worsening state for a long time, making the computing experience ever more hellish.

---

### Post by Golyadkin on 2007-08-24
If you want a very reliable harddrive that practically doesn't get bad sectors, you can try the R.E. series of harddrives made by Western Digital.

---

### Post by gerry1936 on 2007-08-24
Are you sure the disk has bad sectors? I found  when I installed Xubuntu, it was VERY fussy about the state of the hard disk, not from disk faults, but debris left from previous software. I had to run KILLDISK (free, simple erase) before Xubuntu would deign to install.
I expect Ubuntu is the same.

---

### Post by rexy on 2007-08-24
if your sdisk has bad sectors that means it has a truckload of em already, ussually disks hide them from the system by marking them bad themselves. So when you start seeing one bad sector it's already time to scrap it. I  have installed linux on a bad disk once, and while it will work to some extend it is really not worth the effort or trouble.

gerry i would check your disk thoroughly, since a new install formats the drive it's unlikely remaining data will affect the installation process. more likely your disk is faulty.

---

### Post by spydon on 2007-11-12
Yes im pretty sure that it was bad sectors because I got alot of them in:
```
badblocks hda
```
And I got a new harddrive from our IT-support.

---

