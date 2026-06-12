---
title: "Cannot unmount drive for partition..."
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by arnold790609 on 2008-01-22
I read all the appropriate posts and documentation to setup my partition and I just cannot unmount my ntfs drive.  It does have a Triangle warning symbol next to it....partition is labeled /dev/sda1.

I am booting from the liveCD and want to dual boot my laptop....any clues as to how I can complete my partition portion to get ready for install?

Thanks for help from the noob.

---

### Post by newbeeman on 2008-01-22
Why not let the Live CD do the job for you? It's a breeze to install a dual boot.

---

### Post by jesusfreak107 on 2008-01-22
easy. download and burn [http://www.download.com/Parted-Magic-LiveCD/3000-2094_4-10663999.html?tag=lst-8](http://www.download.com/Parted-Magic-LiveCD/3000-2094_4-10663999.html?tag=lst-8)
as an iso file. it is a mini-OS that has a ton of partitioning tools. it is very usefull.

---

### Post by jflarm on 2008-01-22
> **newbeeman said:**
> Why not let the Live CD do the job for you? It's a breeze to install a dual boot.

 Ubuntu install won't work like a "breeze" with the partitions, it has it's flaws.
Try doing it manualy and specify your mount points and partition sizes yourself. That way you'll be sure you are not deleting your xp partition.

---

### Post by arnold790609 on 2008-01-22
As stated in my post I am trying to install from the LiveCD.....when I choose guided and using my base hard drive....it goes straight into Who are you?   At this point aren't I overwriting all data on my Main Hard Drive or will it ask me to actually partition the drive?

---

### Post by arnold790609 on 2008-01-22
I also tried the manual partition through GParted and I am unable to unmount the XP Main hard drive to actually partition it....that is the problem I am having...I don't want to lose XP....afraid that if I just do the guided partition using my Main drive that it will overwrite XP entirely.

---

### Post by tojge on 2008-01-22
It will if you accept the default settings, however, you can and should go for the manual partitioning option of the installer, which should give you the option of using unformatted hard drive space (if any) or resizing your current Win partition to make room for Linux

---

### Post by arnold790609 on 2008-01-22
BAH finally was able to figure out how to read the Warning:  
"Accounting Clusters...Cluster accounting failed at (blah blah blah)
Filesystem check failed Totally 1 cluster accounting mismatches
Error: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was and will be made to NTFS by this software until it gets repaired."

OK....so....run a chkdsk /f?  What does it really want me to do...I ran defrag before I did the LiveCD Boot....anyone?

---

### Post by jesusfreak107 on 2008-01-22
yes, run a chkdsk. you apparently half-formatted it. and, yes, guided partitioning of your main drive will wipe your XP. use[ Partd Magic]("http://www.download.com/Parted-Magic-LiveCD/3000-2094_4-10663999.html?tag=lst-8"), or some other utility to partition it, and then install it on the new partition.

---

