---
title: "dual-boot question: partitioning drives"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by templar66 on 2007-03-31
I am trying to dual boot Ubuntu and XP pro at the moment, and am a little confused about how to partition my drive.  What I had intended on doing was having a partition for the Windows OS, a partition for Ubuntu, and an extended partition for shared files and swap.

When I tried to manually edit partitions, there are 3 partitions shown on my disk.
One is fat16, about 50 Mib.  
The second is ntfs, 230ish Gib.  I assumed this was my windows OS and files.  The third one is fat32 and about 7Gib.  
I have not partitioned this drive before and am a little confused as to what the first and third partitions are.

I assume they are necessary as they are primary partitions, but they are using up 3 of my 4 primary partitions.

Can anyone recommend how to proceed with partitioning space for Ubuntu, swap, etc?

Thanks in advance.

---

### Post by Campingman on 2007-03-31
This gives good advice on the partitions needed for ubuntu
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
As for your existing partitions is one of them a windows recovery partition?

---

### Post by jvc26 on 2007-03-31
All three of them should technically show up in windows allowing you to see what they all are/whats on them. My only thought (presuming that you didnt set up the partitions yourself) are that the FAT ones are system rescue ones (as Campingman suggests) or serve some similar function.
Il

---

### Post by benerivo on 2007-03-31
The 7GB may be a recovery installation of XP. I remember when i broke XP, it booted in to this recovery installation , which was only several GB in size and was a 'clean' installation with no added programs, personal files, etc. I believe when installing XP it creates a small partition that is used to store information about the other partitions, and it may well have something to do with the boot up of windows, so i wouldn't delete it just yet. Theoretically, you should be safe to install Ubuntu as it would create its own grub boot manager so XP could be booted from there. If I were you I would be prepared for the worst (ie. backup important stuff), then load the Ubuntu CD, and use the installer's partition manager to delete the other two, resize the XP one and set up your partitions from there. Remember to defrag with XP first before doing this.

Google for xp recovery partition, and also for xp boot partition for more info on what you have on your hard drive at the moment.

Personally my single drive set up is four primary partitions - xp, kubuntu, shared (as ntfs), and swap.

---

### Post by jvc26 on 2007-03-31
XP doesnt in a normal install create extra drives though for recovery, it only seems to do that when you get the XP factory installed. I have installed XP quite a lot and never ended up with the odd extra partition.
Il

---

### Post by benerivo on 2007-03-31
Yes, the recovery partition is only on from a factory install. I have noticed during XP installs, that it has not used the full capacity of a drive, but brought up a message to say it needs to keep a few MB of space for a partition to control / store info on the other partitions. This may be a boot partition, i'm not sure.

---

### Post by brennydoogles on 2007-03-31
The 7 Gb partition is most likely a recovery partition, which can technically be overwritten if you would like (I actually use the recovery partition on one of my drives as my primary Ubuntu partition).

---

