---
title: "Removed Ubuntu - having problems with the partition"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by VLengoc on 2008-03-01
I have removed Ubuntu from my computer and am planning to merge my Vista partition with my Linux one (formatted, NTFS). What programs can merge partitions for **free**

---

### Post by taurus on 2008-03-01
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by cotcot on 2008-03-01
You can merge your vista partition with the linux partition as well with the same tool. (lol)
We are of course interested in why you left linux. I have the feeling that you left linux before we had the chance to help you. (but this could be a false feeling)
Installing linux on ntfs is not recommended (ext3 is linux native). Maybe that gave you troubles. I always use the gparted livecd (as mentioned by taurus) prior to any new installation.

---

### Post by VLengoc on 2008-03-04
Well, I do love Ubuntu and Linux in general, but I don't really have the time to configure things to work in Linux. I just expect it to work when I install it

---

### Post by mozetti on 2008-03-04
I haven't used Vista, but in XP there was the **Disk Management** tool -- basically a partition editor.

IMO, you should use that tool to delete the old Ubuntu/NTFS-formatted partition, then just enlarge/grow the existing Vista partition to use that space.

---

### Post by MeURi on 2008-03-04
As far as I know, XP built in partitioner can't modify a partition without actually destroy and rebuild it (don't remember properly, and now I'm on Linux :-)), so I'd suggest not to resize the Windows main partition using that tool. Don't know if Vista suffers from the same 'problem'.

VLengoc, aren't there any trial versions of commercial software like Partition Magic, or Acronis Disk Director (I know this two)? Maybe a trial version will suffice

GParted could also be the tool you're looking for, but I never used it for messing with NTFS partitions

---

### Post by VLengoc on 2008-03-06
Partition Magic isn't a true demo; it barely lets you do anything

---

