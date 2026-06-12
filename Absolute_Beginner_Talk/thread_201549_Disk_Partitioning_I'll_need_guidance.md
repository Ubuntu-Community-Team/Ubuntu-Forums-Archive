---
title: "Disk Partitioning: I'll need guidance"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by brn on 2006-06-22
My aging (1998) Linux box has died.  Rather than try to rebuild it, today I bought a used Dell laptop with Windows XP installed on a 20 GB drive.  I ran my Ubuntu '"live" CD where cfdisk told me that there was only one partition on my drive, the whole thing.  The only reference I have for partitioning a disk is the Redhat 6.0 manual I used in 1999 when installing on an empty disk.  I will need help to lead me through this re-partioning process.  The Redhat manual is very thorough but it's reference is to sharing a disk with Windows 98.  I wonder if XP is so benign.  (I don't want to lose it.)  They mention that Windows (98) tries to keep a jealous grip on  the low (boot) diisk area.  What new hazards do I face eight years later?   

QUESTIONS:

How can I identify what disk areas (sector, head, etc.) are safe to create new partitions?  All I can run on the new machine is the "live" Ubuntu. 

How do I extract the 'boot' area from XP control and give it to LILO or the newer loader whose name escapes me right now?

I will be reading and re-reading the old Redhat manual and looking for wisdom wherever I can. Any/all help, encouragement, advice, is appreciated.

---

### Post by aysiu on 2006-06-22
You will, of course, back up your important data and then defragment your Windows partition before doing anything.

This page outlines how the Ubuntu installer works:
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

When you get to the partitioning part, you can right-click a partition to resize it, and you can right-click empty space to create a new partition.

The new partition should be Ext3.

You don't need to worry about a boot area or Lilo. Ubuntu uses Grub and will automatically install it to the MBR to set up a dual-boot with Windows XP.

---

