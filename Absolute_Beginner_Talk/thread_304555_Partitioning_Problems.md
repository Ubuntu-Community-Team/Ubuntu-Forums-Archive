---
title: "Partitioning Problems"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by Taskman on 2006-11-22
I'm trying to dual boot XP with Ubuntu 6.10.  I have a 250GB HDD.  I put XP on a 25 GB NTFS partition.  The rest of the drive is unformated.  Now I'm trying to load Ubuntu 6.10.  Here's what I did for partitions:

/ ext3 15 GB 
swap 2 GB
/data fat32 ~180 GB

I keep getting an error message for the fat32 partition.  It is unable to write to the partition.  I'm I mounting the partition wrong?  I simply typed in /data. Should that work or do I have to choose a mount from the given choices in the installation program?  Needless to say I am very new to Linux so be easy on me.

Thanks

---

### Post by rlozano on 2006-11-22
> **Taskman said:**
> I'm trying to dual boot XP with Ubuntu 6.10.  I have a 250GB HDD.  I put XP on a 25 GB NTFS partition.  The rest of the drive is unformated.  Now I'm trying to load Ubuntu 6.10.  Here's what I did for partitions:

/ ext3 15 GB 
swap 2 GB
/data fat32 ~180 GB

I keep getting an error message for the fat32 partition.  It is unable to write to the partition.  I'm I mounting the partition wrong?  I simply typed in /data. Should that work or do I have to choose a mount from the given choices in the installation program?  Needless to say I am very new to Linux so be easy on me.

Thanks

first, were you successful in installing both windows and Ubuntu?

second, when you said you can't write on the fat32 partition, i would assume that you are already inside Ubuntu.

to correct that problem, you may have to modify your fstab file. visit: [www.psychocats.net](www.psychocats.net) for partition mounting information.

what is the result of your:

1. sudo fdisk -l
2. df -h
2. ls -l

hope this helps...

---

### Post by Smandola on 2006-11-22
Hi Taskman,  
What exactly are you getting for an error ?
is it something like this...
[http://ubuntuforums.org/showthread.php?t=158270](http://ubuntuforums.org/showthread.php?t=158270)

I setup one of my linux boxes with dual boot.  This thread has a number of different links through it.  Check them out and post back.

[http://ubuntuforums.org/showthread.php?t=224907](http://ubuntuforums.org/showthread.php?t=224907)

Hope this can help.
s.

---

### Post by Taskman on 2006-11-22
My problem is in the installation of Ubuntu.  When I get to the "Prepare Mount Points" screen I have four partions listed:

XP NTFS 25GB
swap 1GB
/ ext3 (For Ubuntu)
/files fat32 (shared files)

The three non-windows partitions are unformated, so I need to format them.  This is where the problem arises.  When I click "Install" everything is fine until it gets to formating the fat32 partition then I get an error message. (I'll post the error message in a few hours when I get home from work).

---

### Post by steve.horsley on 2006-11-22
I'm not sure the installer can format fat partitions. It might be easiest to leave that partition unused, complete the installation and then deal with the fat partition from a working Ubuntu.

I would also advise putting the new partitions in an extended partition so you have the option of having more than 4 partitions later.

---

### Post by The Seeker on 2006-11-22
How much RAM do you have? I ask because 2 GB of swap is overkill.

A good rule of thumb is to use twice the amount of RAM you have or 512 MB, whichever comes first.

---

### Post by Taskman on 2006-11-22
How exactly will I deal with this issue after Ubuntu is installed?  Is it possible that I can format the fat32 partition in Windows XP?

---

### Post by bodhi.zazen on 2006-11-22
> **Taskman said:**
> How exactly will I deal with this issue after Ubuntu is installed?  Is it possible that I can format the fat32 partition in Windows XP?

```
mkfs.vfat -n <label_name> <device>
```

This may help: [Partitioning Basics](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by Jamhos on 2006-11-22
Not completely sure about this, but do fat partitions even go that big? Because that would cause problems.

---

### Post by steve.horsley on 2006-11-23
You can format it from a running Linux with this command (use the right device name!!!):
**sudo mkfs.vfat -F 32 /dev/whatever**

I believe that you can create FAT flesystems that big, but that Windows cannot (although it can read them no problem). The reason Windows cannot create large FAT partitions is that MS want to push NTFS instead.

---

