---
title: "dual boot problem maybe??"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by aquilegia on 2006-03-16
I have 2 hdd in my computer
first or primary hdd is 80Gb/windows xp/3 partitions
second hdd is 40Gb/Ubuntu 5.10/no partition=1partitition

And i've install it as dual boot
The problem is Ubuntu can load windows files,but windows xp can't load files in ubuntu,not even detect the drive.

Question:
1.why windows not even detect my second hdd?
2.how to solve this problem?

---

### Post by aysiu on 2006-03-16
Have you tried this?
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Coelocanth on 2006-03-16
Windows can't read the Linux file system. I don't know if there's a way to make it have the ability to do so, but it doesn't even 'see' a Linux partition at all.

If you want to share files between the two OSes, probably the best idea is to create a FAT32 partition to write files to, as both OSes can read and write to that file system.

*edit* Ah, what aysiu said. Iignore me. Shows you what I know...

---

### Post by likwid on 2006-03-19
Has anyone tried this? How well does it work??

---

### Post by dueY on 2006-03-19
I wonder if Windows could see your ext3 drive then if you got a virus on Windows your data on the Ubuntu partition could get messed with?

I have a FAT32 partition that serves as a place to transfer files between Windows and Ubuntu and it works fine for me.

---

