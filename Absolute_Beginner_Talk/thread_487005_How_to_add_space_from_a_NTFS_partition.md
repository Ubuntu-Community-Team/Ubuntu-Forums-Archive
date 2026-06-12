---
title: "How to add space from a NTFS partition"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by adeydas9 on 2007-06-28
Hi,

I just installed Linux and everything worked fantastically with just a little work. Now I can program in Java and C++ and also surf the Internet from Linux. :p

My problem is that I installed Ubuntu just as a test system on a 10 GB partition but now I want to use it full time. However, I don't want to delete Windows as well (which is sitting on a 64 GB partition) since it is required by some programs and games. Is there a  way to take out some space from the NTFS partition of Windows and add it to Ubuntu without messing up data?

Thanks,

Abhishek.

---

### Post by chandler on 2007-06-28
Did you add the partition to the end of the disk?  If so then that'll be tough but doable. ```
sudo fdisk -l
```

---

