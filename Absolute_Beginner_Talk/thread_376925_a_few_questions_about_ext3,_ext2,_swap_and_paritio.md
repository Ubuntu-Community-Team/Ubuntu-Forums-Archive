---
title: "a few questions about ext3, ext2, swap and paritioning"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2007-03-05
ok so here it goes:
when i've installed my ubuntu i didn't actually fully installed by myself... a friend, who recommended me ubuntu told me that when it comes for partitioning, to make one partition ext3 with root in "/" and another one swap of about 500 mb.. now my questions are: is ubuntu installed on that ext3 partition? what for is that swap partition? how can i resize the ext3 partition WITHOUT damaging my files?

---

### Post by lamalex on 2007-03-05
ubuntu is installed on the ext3, swap is virtual memory that linux uses so if you run out it has a place to use temp. storage. you can resize with a program called gparted which will be on the live cd so when you boot to ubuntu you can partition from there, just dont cross into the line where your files are and nothing will be hurt.

---

### Post by steve.horsley on 2007-03-05
If you tell the installer to shrink the windows partition to make room for Ubuntu, then it will create its own partitions which is somewhat simpler than specifying things yourself. Back up your data first, just in case.

The swap partition is used as virtual memory, like a pagefile in windows.

The program gparted can resize and ext3 partition by moving the end of the partition, but it cannot move the start, so you may have to copt the data off, delete, create and format a new partition and copy the data back.

---

