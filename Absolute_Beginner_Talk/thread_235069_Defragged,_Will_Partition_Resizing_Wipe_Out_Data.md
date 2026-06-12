---
title: "Defragged, Will Partition Resizing Wipe Out Data?"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by groberts1980 on 2006-08-12
I'm wanting to resize my Windows NTFS partition and install Dapper 6.06.1 on my Dell Inspiron E1705 laptop. Below is the status of the disk fragmentation after defragging. It won't move that last piece of data to be near the rest. When I resize the partition, will this data be wiped out? I know there's no easy way to figure out what data that is.

I don't have a Windows install, just the restore CD that came with the computer. I've backed up all my critical files, so I can restore the computer if that data turns out to be critical.

Should I be worried?

---

### Post by calvinthomas on 2006-08-12
If you partition using the Ubuntu CD it should not be a problem, it should simply leave that part in tact. I didn't even defrag before installing Ubuntu and repartitioning and I had absolutely no problems. Backing up is a good idea however as there is always a small chance of problems with partitioning

Calv

---

### Post by steve.horsley on 2006-08-12
I think you will find that you can't resize it below that unmoved chunk - maybe 10% at a guess.

You should always assume you will lose data, and make backups first.

---

### Post by byen on 2006-08-12
It is very hard to predict and say that your partitioning will go well. But I will say this... I have done this twice on my computers and both the times I have not had any issues. I managed to create a partition without loosing any data or any damage to my XP install. But this does not guarantee that it will work on your setup as well... there are quite a few threads here where this did not work.... So all you can do is just back up and take the plunge... 
Goodluck mate.. Let us know how it went!
regards,
byen

---

### Post by djsroknrol on 2006-08-12
The best thing you can do is defrag the MS partition before you try to resize a partition for your Ubuntu install..I've never ha a problem doing it that way...

---

### Post by az on 2006-08-12
> **groberts1980 said:**
> 
Should I be worried?

Parted and libntfstools are pretty paranoid.  They will refuse to do anything if they risk data loss.

Probably the worst thing that will happen is that it will refuse to partition.

---

