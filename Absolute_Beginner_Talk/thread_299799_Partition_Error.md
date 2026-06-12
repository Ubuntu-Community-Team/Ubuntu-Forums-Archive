---
title: "Partition Error"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by ShardOfNarsil on 2006-11-14
I am trying to make a dual-boot machine with a preexisting Xp installation but it just won't work. I choose to make a 10 gig ext3  and a 1 gig linux-swap partition. I then hit "apply" and all it says is "error" with no explanation. I am using the built in partition editor in the live cd.

---

### Post by PPAAUULL on 2006-11-14
Are you resizing or putting it on a new drive?

---

### Post by ShardOfNarsil on 2006-11-14
I'm trying to resize the drive XP is on.

---

### Post by ReaderRat on 2006-11-14
> **ShardOfNarsil said:**
> I'm trying to resize the drive XP is on.
[**Resize Partitions**](http://www.ubuntuforums.org/showpost.php?p=1642649&postcount=2)
[**Partitioning (XP & Ubuntu)**](http://psychocats.net/ubuntu/partitioning)

---

### Post by moshuptrail on 2006-11-14
One gotcha.
If your NTFS partition has any bad blocks gparted won't be able to re-size it.  But it won't say why.  It just says, "failed" or something equally inane.  To re-size the partition in that case, use ntfsresize.  But THAT is not a task for the feint of heart.

---

