---
title: "Partition and formating problem"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by hybirden on 2007-11-21
I was trying to format a drive to use as a storage drive, but i must have goofed things up alittle cause now it shows 2 partitions both the same size of the drive!  I have tried deleting them both but as soon as I do it comes right back. (see attachment)  I am pretty new to Ubuntu so any help will be greatly appreciated.

Thanks, 
Hybirden

---

### Post by taurus on 2007-11-21
Your /dev/hdb1 is an extended partition so you need to create a logical partition which you have, /dev/hdb5.  If you don't want to use extended partition, delete /dev/hdb5 and convert /dev/hdb1 to primary partition.

---

