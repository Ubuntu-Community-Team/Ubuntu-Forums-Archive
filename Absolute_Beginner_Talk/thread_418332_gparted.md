---
title: "gparted ?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2007-04-22
I have a tri boot system and want to repartition and format the drive.  Does gparted partition and format the whole hd or just repartition?

---

### Post by Bachstelze on 2007-04-22
Could you please describe more precisely what you want to do ?

---

### Post by jhenager on 2007-04-22
Add/remove partitions
format partitions

Pretty much whatever you want.

---

### Post by 3rr0r on 2007-04-22
Tri boot system.  I want to format the entire drive, then repartition it using gparted.  I don't know how to go about formatting in ubuntu.

---

### Post by Bachstelze on 2007-04-22
I think something is not clear there. Formatting a device means creating an empty filesystem on it and formatting an entire drive is definitely not something you want to do. What you want to do is delete all the partitions on the drive, create new ones instead and format them using various filesystems. GParted will let you do that.

---

### Post by Happy_Man on 2007-04-22
Boot from a LiveCD and go to System --> Administration --> GNOME Partition Editor.

---

### Post by 3rr0r on 2007-04-22
> **HymnToLife said:**
> I think something is not clear there. Formatting a device means creating an empty filesystem on it and formatting an entire drive is definitely not something you want to do. What you want to do is delete all the partitions on the drive, create new ones instead and format them using various filesystems. GParted will let you do that.


Yes, I want to delete everything on the entire drive, then repartition.  For my tri-boot 2 new releases are out that I want to install.  So I would rather wipe everything clean than install over (fiesty and backtrack2.0). I think I see the steps.  Delete patitions, create new ones, then format them to specific types.  Will this cleanly erase all the previous data (empty/clean partitions)?

---

### Post by 3rr0r on 2007-04-22
also, generally linux is ext3 ? 
swap should be ext2?

---

### Post by Happy_Man on 2007-04-22
Yep, blank as the day it was bought.

When you install Ubuntu, it will make a swap partition for itself automatically. If you're putting a Windows system on, DO THAT FIRST. Then your other OS's.

---

### Post by n3tfury on 2007-04-22
no offense, but i find it a bit odd that you're having these types of questions yet you use Backtrack.

---

### Post by Bachstelze on 2007-04-22
Yes. Also, when you create a partition, you can specify a filesystem so GParted will format it for you with no additional step required.

Linux can be installed on various filesystems, ext3 is the most common nowadays. swap is swap, it uses it's own filesystem, which is not ext2.

---

### Post by 3rr0r on 2007-04-22
> **n3tfury said:**
> no offense, but i find it a bit odd that you're having these types of questions yet you use Backtrack.

I jumped into linux by jumping onto backtrack.  I focused most of my time in learning the tools and how to use them in/against various environments.  I did not spend much time learning what can be called, the basics of linux.  That is what my ubuntu partition is for.  I have used backtrack solely in the instruction of network  and computer security.

---

### Post by n3tfury on 2007-04-22
> **3rr0r said:**
> I jumped into linux by jumping onto backtrack.  I focused most of my time in learning the tools and how to use them in/against various environments.  I did not spend much time learning what can be called, the basics of linux.  That is what my ubuntu partition is for.  I have used backtrack solely in the instruction of network  and computer security.

understandable if the questions you were asking were Linux-specific ;)

---

