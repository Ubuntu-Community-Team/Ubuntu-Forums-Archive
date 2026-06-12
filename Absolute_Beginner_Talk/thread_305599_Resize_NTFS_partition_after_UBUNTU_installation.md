---
title: "Resize NTFS partition after UBUNTU installation"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by EGE-FB on 2006-11-23
Hi, 

I already have Ubuntu installed on my computer. 

My partitions are:

NTFS - 45 gb 
ext3 - 5 gb
swap - 2 gb
ext3 - 45 gb 

I want to resize my NTFS partition and my 45 gb ext3 partition so that I can expand my NTFS partition. How can I do this? 

Thanks

---

### Post by izmaelis on 2006-11-23
Download and burn GParted Live CD and use it to manage your partitions the way you want. It works a little bit like PartitionMagic or smth.

---

### Post by EGE-FB on 2006-11-23
Ye, I already have the Live CD of GParted. The thing is I cannot resize my NTFS partition. The "unallocated" space comes after my last partition (which is the ext3 45 gb one) and I can only make adjustments to that particular partition.

---

### Post by EGE-FB on 2006-11-23
Help?

---

### Post by ajgreeny on 2006-11-23
The ntfs partition is presumably the first on the disk?  All the others are next to that so move them one by one to the end of the disk, leaving the unallocated space next to ntfs partition, then enlarge the ntfs partition.

I think moving partitions is only possible with newest version of gparted live CD so get that if needed (0.3.1-1)

Good luck and let us know if it works.

---

