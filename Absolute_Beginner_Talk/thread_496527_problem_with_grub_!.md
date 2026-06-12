---
title: "problem with grub !"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by chresto on 2007-07-09
Ok guys, here is my problem :

first of all, I 've got 2 hard disks. one has a partition in ntfs with windows xp, and the other, has 2 partitions, 1 swap, 1 ext3 with ubuntu linux. yesterday, in my attempt to install gentoo, I 've made a mistake and deleted all the partitions I had made in my first disk, along with the partition that had win xp. so, afterwards, after making some research, I tried to restore my lost partition with testdisk and I think I succeeded in doing so. so, today, I have my win xp os, and my ubuntu os. but, sth has gone wrong with the grub ! when I use my disk which has the xp os, as primary, while booting, it starts in xp without showing any grub window to choose the os . when I use the disk with the ubuntu os as primary, grub starts, but ! when I choose ubuntu it shows an error 17 : unable to mount partition, and when I choose to start in xp, it says, loading/starting grub and I get back to the first page. in other words, sth has gone wrong with the grub ! I tried some tricks with super grub whatever and through a terminal, but nothing happened :/ I want to leave reinstallation of ubuntu as a last resort :x

Any help would be great :confused:

---

### Post by felicity on 2007-07-09
In the grub boot screen try editing the line with hd0, 0 (or hd1, 0 or whatever it may be in your list) by typing e, and changing the hd0, 0 to hd1, 0 or another combination depending on what your exact partition scheme is.

---

### Post by chresto on 2007-07-09
Well, after experimenting a little more, I managed to start my grub manager, and so far, I can start ubuntu without any problem. but ! now a new problem occured : ubuntu can't mount the disk with the xp os inside and when I choose to start xp from the grub manager, I get the grub terminal or whatever it is like : grub>
this is getting more complex as time passes ;_;

---

### Post by felicity on 2007-07-09
Change the options on the Windows grub menu entry just like you did the Ubuntu entry. Maybe  hd1, 0 or h1, 1, depending on which your Ubuntu line says, it's probably the one opposite it. 

Or here is info to mount the ntfs in Ubuntu:

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")

---

