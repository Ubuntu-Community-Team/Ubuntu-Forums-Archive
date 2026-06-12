---
title: "Another Partitioning/Dual Boot Question"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by Spondy on 2006-07-08
First I must say this is great forum with patient, polite and helpful folks answering what may be extremely repetative questions to lost in the dark linux noobs. Your efforts are appreciated.  

Now for my noob question...I have XP pro installed on a 250 sata drive in my system.  I have an additional 400g pata(ide) drive which I wish to install Dapper Drake on and dual boot.  I have read in the forums that it may be tricky at best to get this working properly (apparently some grub issues with IDE SATA mixing). 

Should I install Dapper to the sata drive and use the ide with additional partitions for storage or is it less risky to install dapper directly to the IDE drive?  Is the partition software on the live cd non-destructive like partition magic(therefore saving my XP install and allowing a dual boot)?  I don't want to hose my XP setup.:( 

Thanks for any info....

---

### Post by ifokkema on 2006-07-08
Hi,

I don't use SATA disks myself (yet), so I can't comment on your main question, sorry.

But as to the partitioning:
> **Spondy said:**
> Is the partition software on the live cd non-destructive like partition magic(therefore saving my XP install and allowing a dual boot)?  I don't want to hose my XP setup.:(
The partitioner on the Live CD is real nice. I suggest you first check on Windows, where your C, D, etc drives are, on what disk. Then in the Live CD partitioner, you can see all partitions listed. You can then start modifying/deleting/creating partions one by one, so you don't have to loose your Windows install. After install, Grub will automatically search for other OS on your disk and include that in the boot menu.

---

