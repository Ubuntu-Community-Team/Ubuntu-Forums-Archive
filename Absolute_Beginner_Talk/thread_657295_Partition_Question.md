---
title: "Partition Question"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by mjheagle8 on 2008-01-03
I am trying to install ubuntu 6.06 on my pc.  I have windows xp installed.  I have a 80 gb hard drive that I have never partitioned before.  There were three partitions, all primary, by default, one 70 gb, one 3gb, and one 80 mb.  I resized the 70 gb partition to 50 gb to leave room for linux, with no problems.  Now, I cannot install linux because when I try to create swap space and linux space, I need two primary partitions and the drive will only let me have a maximum of four primary partitions.  I am running xp now.  What can I do to resolve this problem?  Thanks for your help!

---

### Post by nick_h on 2008-01-03
You will need to create an extended partition and make both the linux and swap partition logical drives within it.

---

### Post by mjheagle8 on 2008-01-03
thanks!  it will still boot from the extended partition right?

---

### Post by nick_h on 2008-01-03
yes

---

### Post by The Cog on 2008-01-03
Even easier - just delete that 4th partition and tell the Ubuntu installer to user the free space. It will make its own partitions as it sees fit.

---

