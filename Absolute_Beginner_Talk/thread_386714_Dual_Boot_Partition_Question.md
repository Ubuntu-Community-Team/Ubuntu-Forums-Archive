---
title: "Dual Boot Partition Question"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by ARS on 2007-03-17
I am looking to set up a dual boot system with Windows XP and Ubuntu.  Windows is already installed and I have already set up four partitions on my hard drive.  
The partitions are:
1. 100GB for Windows
2. 20GB for Windows Backup
3. 20GB for (nothing at the moment)
4. 100GB for files etc.

I was thinking about installing Ubuntu on the 100GB partition, but from what I have looked at you need to set up multiple partitions for Ubuntu to work well.  It seems to me that you need a base partition, a swap partition, and a user partition.  Is this right and how big should each be?  Also if I need to reformat the 4th partition into smaller pieces can I do that without affecting the other 3?  Installing Ubuntu on the 4th partition will not mess up Windows will it? Please help me here, help is appreciated.

---

### Post by mikewhatever on 2007-03-17
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

If all four partitions are primary, you'll need to delete one to create an extended partition and then make Ubuntu partitions logical.

---

