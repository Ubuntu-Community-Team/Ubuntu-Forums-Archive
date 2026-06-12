---
title: "general hard drive questions"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by parts-man73 on 2007-05-24
I just installed feisty on my computer a couple weeks ago. It's a dual boot with windows XP. This install went alot smoother than the last time I tried out Ubuntu. No problems whatsoever with the install.

My 2 questions...

I've have some instances when the computer has frozen/locked up. Ussaully while using Firefox. ctrl-alt-backspace will normally get me back to a login screen. 

Is there a way to scan the hard drive for errors after this happens, or as a normal maintaince? I am just looking for a way to keep the system running smoothly. Something similar to ScanDisk and/or Defragment?

Second question. My NTFS drive that Windows is installed on (I have 2 hard drives, one is for windows, one for Ubuntu), I can see it, and read files from it. But it first requires the root password to access it. After which, it shows on my desktop. Why do I need to type in a password each time? This is a single user setup.

Also, it won't let me write anything to the NTFS drive.

Thank you in advance,
Brian

---

### Post by Sparkster185 on 2007-05-24
1. fsck will check a filesystem for errors.  It's pretty straightforward to use.

2.  To write to an NTFS partition, you need to install ntfs-3g.  I believe there should be an application in your Add/Remove Programs list to manage NTFS partitions.  Try using that.

---

### Post by LaRoza on 2007-05-24
> 
Second question. My NTFS drive that Windows is installed on (I have 2 hard drives, one is for windows, one for Ubuntu), I can see it, and read files from it. But it first requires the root password to access it. After which, it shows on my desktop. Why do I need to type in a password each time? This is a single user setup.

Also, it won't let me write anything to the NTFS drive.


You can read the NTFS drive, but can not write to it without ntfs-3g, search the forums (Write to NTFS). Asking for a password is normal, for security reasons. Would you want people using you computer be able to perform administrative tasks on Ubuntu? I have a similar set-up, two hard disks, two os's.

If you want to make sharing easier, you could make a FAT32 partition on the Windows disk and put everything you want to share in there.

---

### Post by dbott67 on 2007-05-24
> **parts-man73 said:**
> Is there a way to scan the hard drive for errors after this happens, or as a normal maintaince? I am just looking for a way to keep the system running smoothly. Something similar to ScanDisk and/or Defragment?

**fsck** (file system check)
```
man fsck
```
for all the gory details.

> **parts-man73 said:**
>  Second question. My NTFS drive that Windows is installed on (I have 2 hard drives, one is for windows, one for Ubuntu), I can see it, and read files from it. But it first requires the root password to access it. After which, it shows on my desktop. Why do I need to type in a password each time? This is a single user setup.

Also, it won't let me write anything to the NTFS drive.
 
By default, NTFS partitions are mounted as read-only.  A number of months back, writing to NTFS partitions was considered 'experimental' and you faced potential problems if you wanted to write to NTFS.

I have not checked recently, but here is a thread that will ge you going:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

-Dave

---

