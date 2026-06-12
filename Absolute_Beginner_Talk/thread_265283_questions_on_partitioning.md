---
title: "questions on partitioning"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by Cruz on 2006-09-25
Is there a reason why I shouldn't create three primary partitions (/, swap and data)? Why would I want to create one primary and one extended and put the swap and the data as logical partitions into the extended partition?

Why doesn't the partitioner that comes with ubuntu apply names to the partitions? Cann I add names with a different tool later without screwing up the partitions I created?

---

### Post by Cruz on 2006-09-25
And what happens if I mount more than one device on the same mount point? (if it's possible at all)

---

### Post by TheMono on 2006-09-25
I don't think you can mount two things at the same point - possibly if they were read-only? - but if you tried to write, you may get interesting results. You can still mount within another mount - so, say you have an external HDD with a Data and a Movies partition, you can mount one at /media/Data/ and the other at /media/Data/Movies if you wanted.

As far as "Is there a reason why I shouldn't create..."
Is there a reason why you should?

You can only have 4 primary partitions to a drive, so given the popularity of dual-boot, weird scanning tools in their own partitions, and stuff like that, you may as well leave it in the extended. Or, read up on LVM.

---

### Post by CatKiller on 2006-09-25
> **Cruz said:**
> Is there a reason why I shouldn't create three primary partitions (/, swap and data)? Why would I want to create one primary and one extended and put the swap and the data as logical partitions into the extended partition?
Habit, mostly, I think. Certainly either old disk controllers, or old DOS, couldn't handle having more than one active primary partition on a drive, so it was common practice to have one primary partition and others in extended partitions. Any other primary partitions couldn't be read. I don't think it matters any more.
> Why doesn't the partitioner that comes with ubuntu apply names to the partitions? Cann I add names with a different tool later without screwing up the partitions I created?
GPartEd, the partitioner that I believe the installer uses, can't name volumes in FAT or NTFS. There's not a huge amount of point in labelling ext filesystems, AFAIK. So it doesn't bother. I've labelled FAT volumes in Windows with no problems for either Windows or Ubuntu.
> **Cruz said:**
> And what happens if I mount more than one device on the same mount point? (if it's possible at all)It's not advisable ;) What I think happens is that the second device takes the mount point until you unmount it, and then the first is there without remounting. I don't know if it will work properly or not. I've just had subfolders in the mount point - /data/fat and data/ntfs, for example.

---

### Post by Cruz on 2006-09-25
I think labeling a partition makes it easier to see what's what when you are looking at your drives with a partition manager. I used QTParted a lot in the last few days but I didn't find a way to relabel a partition (could be stupidity). Gparted should be pretty much the same.

---

