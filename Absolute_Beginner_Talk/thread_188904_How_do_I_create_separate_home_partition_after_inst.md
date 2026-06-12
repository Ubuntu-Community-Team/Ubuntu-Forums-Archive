---
title: "How do I create separate /home partition after install"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by stevanbt on 2006-06-04
Hi all,
I've just upgraded to Dapper - which is running very well.  My problem is I installed everything onto one HD partition (no separate /home partion), I've read several times that it would be better to create / and /home partitions.

My question is - can I create a /home partition but keep all the user data I currently have, or is it not worth the pain?  Output from fdisk -l:-
```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        7288    58540828+  83  Linux
/dev/hda2            7544       19457    95699205   83  Linux
/dev/hda3            7289        7543     2048287+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7476    60050938+   b  W95 FAT32

```

So I'll need to resize /dev/hda2 to make room for a new partition.  But qtparted won't allow me to resize it, the menu option is greyed out.  If push comes to shove I could use /dev/hda1, but I'd prefer to leave it alone.

Thanks in advance, Steve.

---

### Post by rbalfour on 2006-06-04
Is /dev/hda2 mounted when you try qtparted?

You need to unmount the drive before resizing.

Note:
Always BACKUP your data before trying this operation.

---

### Post by stevanbt on 2006-06-04
Unfortunately yes.  I installed Ubuntu on /dev/hda2.

If I need to unmount the drive before resizing can I use the Live CD?

---

### Post by tc10b on 2006-06-04
[QUOTE=stevanbt]Unfortunately yes.  I installed Ubuntu on /dev/hda2.

If I need to unmount the drive before resizing can I use the Live CD?[/QUOTE]
The Dapper Drake Disk runs the partioner from the Disk so your drive will be unmounted, so it should work fine.

---

### Post by stevanbt on 2006-06-04
Ok I'll give it a go with the Live CD.  But what do I need to do once I've resized /dev/hda2?  I'm guessing something like this:-

Create a new partition as ext3?
Copy data from /home directory on /dev/hda2 to new partition
Rename old /home directory on /dev/hda2
Put an entry in /etc/fstab (I certainly need help with this) something like:-
```
/dev/hda3       /home               ext3    
```
Reboot

Does that cover everything?

Thanks, Steve.

---

### Post by aysiu on 2006-06-04
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by beameup on 2006-07-22
Careful, I just tried this and it looks like I may have hosed my system.

[http://www.ubuntuforums.org/showthread.php?t=221049](http://www.ubuntuforums.org/showthread.php?t=221049)


I just "had to mess with it" LOL.  ](*,)

---

### Post by djsroknrol on 2006-07-22
I would suggest the GParted live CD or Disk Drake to do the partitioning...I've heard that the partitioner on the live CD is not very reliable..

---

