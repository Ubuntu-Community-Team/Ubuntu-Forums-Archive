---
title: "Dual Booting and Partitions"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by CeeDub on 2006-09-16
I recently installed Ubuntu and I just realized that I partitioned a little too much on my Windows partition.  Is it safe to re-partition so Ubuntu would have more hard drive space, or is there a good chance I will lose my stuff?

---

### Post by spur on 2006-09-16
Risky. Back up first. If it's really a concern then I'd do it. I purchased a partition manager as this kind of thing seems to happen to me a bit and I like to keep control over things when I'm trying to 'fiddle' with my partitions. Seriously though ubuntu runs so well why do you need the extra space? And xp is  a space hog so you might find if you change it you will only want to change it back.

---

### Post by radj2 on 2006-09-16
Be careful I lost my windows partition,but it was 98se didnt use it much

Good luck

---

### Post by BlacKat_K on 2006-09-18
Hey i'm running only Ubuntu and i didnt make any partitions or such.But now i'm thinking of installing XP for those little programs that wont run on linux.Do i need to do anything special,can i install xp without partitioning or would it erase my ubuntu instalation?Basically i want to know how its done :)

---

### Post by cotcot on 2006-09-18
Before you resize the windows partition make sure hat you backup and that you defragment the ntfs partition.

---

### Post by crokett on 2006-09-18
> **BlacKat_K said:**
> Hey i'm running only Ubuntu and i didnt make any partitions or such.But now i'm thinking of installing XP for those little programs that wont run on linux.Do i need to do anything special,can i install xp without partitioning or would it erase my ubuntu instalation?Basically i want to know how its done :)

Unless you formatted your existing partitions to NTFS or FAT at install, you can't install XP to your ubuntup partitions anyway.  If you want to install XP w/o losing ubuntu, you need a partition manager to resize the partitions  so you have space to create a new partition for XP.

---

### Post by BlacKat_K on 2006-09-18
I understand one of the partitions is still NTFS.I didnt do anything when i installed Ubuntu though...

---

### Post by bulldog on 2006-09-18
> **BlacKat_K said:**
> I understand one of the partitions is still NTFS.I didnt do anything when i installed Ubuntu though...

sudo fdisk -l should show them all 

Look if there's a NTFS partition

---

