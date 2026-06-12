---
title: "Guided Resize SCSI (0,0,0)"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Avinash4 on 2007-04-28
Hey, I am installing ubuntu feisty, and I currently have one 120gb physical drive, partitioned into two ntfs partitions 40gb +80gb. I currently use the 40gb C: for windows, and 80gb D: for storage. I would like to use 15gb from the C: to install feisty, but  I cannot lose any of my files, or windows install. When I boot from the ubuntu disk, I see the install icon on the ubuntu desktop, and I click it. At the partitioning step, which one should I choose so I DO NOT lose any data?

Guided Resize SCSI (0,0,0) followed by a long bar with %? What does this bar mean?

---

### Post by Sef on 2007-04-28
> At the partitioning step, which one should I choose so I DO NOT lose any data?

**Back up** your data first.   There is no 100% guarantee that whatever method you choose to partition will not cause you to lose your data.

---

### Post by annda on 2007-04-28
defragment your c: first. or do it twice. back up life-or-death files. it is ALMOST impossible to lose data. even if you mess up the partition table, you can use the live cd to repair it easily. but hings can happen.

choose manual partitioning to be able to assign 15 GB to ubuntu.

read this:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

if it's too complicated, use the bar to resize the windows partition to some 62% - that will be about 25 GB. the rest will be used by ubuntu.

---

### Post by paparucino on 2007-04-28
> **Avinash4 said:**
> I choose so I DO NOT lose any data?

Follow the advices of other users then mine :-)
Use 15gigs from D: to install Ubuntu
The problem to use part of C: is that Windows puts its own file in a random order on the disk and they canno be moved while defragging. This may cause problems. 
So, IMHO, it's safe to use a partitions without system files.

---

