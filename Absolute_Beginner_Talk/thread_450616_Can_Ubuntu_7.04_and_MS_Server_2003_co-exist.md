---
title: "Can Ubuntu 7.04 and MS Server 2003 co-exist"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by timdoc1 on 2007-05-21
I want to dual boot on my newly built PC.  I already have Server 2003 running.  I created all these FAT32 partitions (except H:):

C: Server 2003  10GB
D:  LINUX         102MB
E: ORACLE1       32GB
F: ORACLE2       32GB
G: All-ACCESS    32GB
H:100GB NTFS
I: LINUX ROOT  32GB
J: LINUX HOME  32GB
K: LINUX VAR     10GB
J: LINUX SWAP    4GB

C and D are on the primary partition the rest are Extended partition.

Can I install ubuntu onto D: without destroying Server 2003 install.  Am I doing this right.  BTW the drives (D-J) are only named -no data is on them, but should show how I intend my install to be.

Thanks,
tim

---

### Post by Cypher on 2007-05-21
All that looks fine, and yes you can install Ubuntu without harming your Server installation. You'll want to re-format Linux Root/Home/Var to be EXT3 and set the Linux Swap to be of type "swap". So in the Ubuntu installation, choose to manually partition the drive and just use the partitions as they're already made just changing the type..

**Also..**
You'd want to mount the partitions as so:
D: -> /boot
I: -> /
J: -> /home
K: -> /var
J: SWAP

---

### Post by timdoc1 on 2007-05-21
Thanks!!!

---

