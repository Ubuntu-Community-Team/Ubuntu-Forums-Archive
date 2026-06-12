---
title: "OMG.. Partition Magic!"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by ubunick on 2005-12-15
What is up with this!? I tried partitioning space for linux and then it messes up, and now my 120GB says its 92GB, and that's not the TOTAL SIZE (which is actually 114GB).  I don't understand how to fix this or reverse this, but seriously, I need HELP.

---

### Post by adwait on 2005-12-15
Where does it say that? In windows? If partition magic has created linux file systems on some part, windows can't see that. If you want to delete them, run partition magic....it will show all the partitions including the Linux ones.

---

### Post by az on 2005-12-16
[QUOTE=ubunick]What is up with this!? I tried partitioning space for linux and then it messes up, and now my 120GB says its 92GB, and that's not the TOTAL SIZE (which is actually 114GB).  I don't understand how to fix this or reverse this, but seriously, I need HELP.[/QUOTE]

This is not the first time that a windows partitioning tool has borked a partition table with a linux file system on it.  I do not recomend using anything other than parted.  If parted cannot do it, you are on your own.

You can probably fix the partition table with parted or some other application.

You can boot the install cd, let it detect your hardware and then CTRL-ALT-F2 to a console and run parted

parted /dev/hda

erase the partition table and the try to rescue the partitions you had on the disk.  If you tell it more or less where they started and finished, it can salvage them for you.

---

### Post by thezerogroup on 2005-12-16
PM sucks for creating linux partitions, use only for FAT, or NTFS!

---

