---
title: "Some questions"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by infin?ty on 2006-07-03
1.) When i run fsck it says running fsck on mounted volumes can be dangerous.. wat is the danger and how to run fsck successfully?

2.) I have windows installed on FAT32 system, but ubuntu has mounted it as a read only volumes, how do i change it R/W?

---

### Post by Jagot on 2006-07-03
After every 30 boot Ubuntu will check the disk anyway so you don't need to run fsck

And with regards to the partitions, read this:

[https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html](https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html)

---

### Post by wolfmaniac on 2006-07-03
ans to the 20 ques

> sudo mount /dev/sda6 /media/windows/ -t vfat -o iocharset=utf8,umask=000 


change sda6 to ur disk

---

