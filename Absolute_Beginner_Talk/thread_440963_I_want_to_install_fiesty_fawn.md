---
title: "I want to install fiesty fawn"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by John82 on 2007-05-12
I already have ubuntu 6.06 on a Dual boot system with windows XP on another partition. I want to upgrade now, except I dont want to save any files or any setting of ubuntu 6.06 as I completely messed that one up and made it look very ugly(im a newbie). I have the both the live cds of both the new ubuntu as well as the old ubuntu. How can I do this. I would like to overwrite ubuntu 6.06. And also have my windows stay where it is.

---

### Post by Najand on 2007-05-12
Use Fesity Fawn Live CD and format your old Dapper partition and install it there.
It is much easier than any upgrade and all your settings would be removed.

---

### Post by John82 on 2007-05-12
How do I check where my old ubuntu is installed I mean what partion?

---

### Post by Najand on 2007-05-12
Well... you can find it using:
```

$ sudo fdisk -l

```
but it is not important. Becuase it is probably the only EXT3 partitions on your harddisk and when you try to install ubuntu (if you select "manual partitioning") you can find it there. I think you don't want to repartition your harddisk again. So, you don't need to change partition layout and then select your current ext3 to be mounted as root partiton ("/") and get formatted.

---

