---
title: "&quot;missing&quot; data after partitioning?"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by papermoon on 2007-08-07
my windows partition is 61.4 Gb and my linux partition says it has about 8 GB free. all i have on the linux partition is ubuntu, i just installed it today....

the thing is i have a 75.4 GB HDD... where is the missing 6 gb or so? :S

EDIT: does ubuntu pick up so much space?

---

### Post by original_jamingrit on 2007-08-07
A clean install of Ubuntu should not take 6 gigs.  Do you use a swap space partition?

---

### Post by ayenack on 2007-08-07
NTFS/FAT32 are not effcient in the way that they use space so your windows drive is most likely the reason for the missing 6GIG. If you install 300GIG drive and partition it with XP as NTFS/FAT32 you will end up with a 290GIG drive whereas if you were to patition it with ext3 you would end up with a 300GIG drive.

Ubuntu or any GNU Linux OS will pick up as much space as you can throw at it with no problems at all.

---

### Post by papermoon on 2007-08-07
if i, at some point wanted to do away with this partitioning and then reformatted my drive into 1 partition... would i get back the lost space?

---

### Post by ayenack on 2007-08-07
If you mean would you get back the 8GIG partition Ubuntu is on back, then yes you would. You would have to re-format it as either NTFS or FAT32 for Windows XP to be able to use it though and it would be a new partition of 8GIG under WinXP not part of your current XP partition.

---

