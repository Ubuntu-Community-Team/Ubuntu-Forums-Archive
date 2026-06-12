---
title: "[SOLVED] Xp Boot Problem After Ubuntu Insattl"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by stgiaf on 2007-09-13
After installing Ubuntu in an existing Windows Installation (different Partition) , windows doesn't boot. It goes on the loading screen and then reboots.
After a research in this forum I did many actions as fixbmr etc.
The fixboot command raises an error.
I decided to re-install windows, but in the screen where you select the partition in which you would like to install windows I see than in the place of c: is the ubuntu partition with volume c:.
It seems like Ubuntu has changed the NTFS partition.
I recognized it from the size because I manually created the Ubuntu partition to have a 10GB size.

Is there any software tha analyzes and fixes file systems?

---

### Post by mikeyphi on 2007-09-13
You could try 'testdisk' - install through synaptic.

---

### Post by ukripper on 2007-09-13
Try my guide if that could fix your booting problem -
[http://ubuntuforums.org/showthread.php?t=466234](http://ubuntuforums.org/showthread.php?t=466234)

---

### Post by stgiaf on 2007-09-13
The problem is that Xp Cd does not recognize c.
If I give dir for example on c: into the recovery mode, i get an error message. 
From the other side, Ubuntu recognizes the partition as an NTFS partition and i can see the files in there.

Also, fdisk -l shows the partition /dev/sda1 as FPS if I can remember well..

---

### Post by mikeyphi on 2007-09-13
Is this correct?
You can read windows files via ubuntu but can't read ubuntu files via windows?
If so you need to install Ext2 IFS in windows to allow you to read ubuntu from windows: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Terl on 2007-09-13
> **stgiaf said:**
> After installing Ubuntu in an existing Windows Installation (different Partition) , windows doesn't boot. It goes on the loading screen and then reboots.
After a research in this forum I did many actions as fixbmr etc.
The fixboot command raises an error.

I assume you mean the fixmbr gave you an error?  If so, do you recall what it was?

> I decided to re-install windows, but in the screen where you select the partition in which you would like to install windows I see than in the place of c: is the ubuntu partition with volume c:.
It seems like Ubuntu has changed the NTFS partition.
I recognized it from the size because I manually created the Ubuntu partition to have a 10GB size.

Is there any software tha analyzes and fixes file systems?

This last bit makes me wonder.  Are you certain Ubuntu installed in the partition you made for it?  When you went to reinstall windows, was any NTFS portion showing?  If not you may have overwritten windows and you would have to start over.  Or did I misunderstand your descriptions...

---

### Post by stgiaf on 2007-09-13
> **Terl said:**
> I assume you mean the fixmbr gave you an error?  If so, do you recall what it was?



This last bit makes me wonder.  Are you certain Ubuntu installed in the partition you made for it?  When you went to reinstall windows, was any NTFS portion showing?  If not you may have overwritten windows and you would have to start over.  Or did I misunderstand your descriptions...

I didn't overwritten windows as the files in NTFS partition are intact.
No, the Windows Setup does not see any NTFS volume. That is the strange.

---

### Post by Terl on 2007-09-13
How can you see they are intact if the windows cd does not see them?  When you boot with the xp cd, press R to go to recovery.  Does it show a windows install?  If so enter that one (Usually press 1).  Then you do the fixmbr command.  You will get a warning about overwriting a loader but allow it.  If it shows no install of windows something is wrong....

---

### Post by stgiaf on 2007-09-13
> **Terl said:**
> How can you see they are intact if the windows cd does not see them?  When you boot with the xp cd, press R to go to recovery.  Does it show a windows install?  If so enter that one (Usually press 1).  Then you do the fixmbr command.  You will get a warning about overwriting a loader but allow it.  If it shows no install of windows something is wrong....

I can see that files are intact inside Ubuntu where the partition has been mounted.
The Xp cd can't see this partition although it is ntfs.

---

### Post by stgiaf on 2007-09-13
I found it!!!!
It was a partition OPUS which was overlap with the ntfs.
I ran testdisk and i fix the problem.

Thanks mikeyphi and all of you for your support and time!

---

