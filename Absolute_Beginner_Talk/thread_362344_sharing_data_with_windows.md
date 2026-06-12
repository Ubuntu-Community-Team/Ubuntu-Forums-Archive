---
title: "sharing data with windows"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by mattjames on 2007-02-15
Hi all.
I'd like to give Linux a try, but first I have a question.
I can put 3 hard drives in my PC. One for Windows XP (which I need for games), one for Linux and a 250GB drive for my music, etc which I would like to be usable (i.e. read & write access) by both Linux and XP.
But Linux can't write to NTFS (or so I've read) so what file system should I use on my 'shared' drive?

Matt

---

### Post by louis_nichols on 2007-02-15
The best solution is FAT32. Linux can reliably read/write to it. It has some limitations, though (no DVD ISOs for example, also fragmentation issues), so you have to think it through. Another solution would be to use ext2 or ext3, which is the native for Linux, then installing the needed driver under windows. The driver is called [ext2ifs]("http://www.fs-driver.org/") (<- link to site). I think this solution is even better.

Write support for NTFS under Linux is here. It's beta, but improving. :)

---

### Post by shanepardue on 2007-02-15
Yeah writing to NTFS is beta, but just so you know, I've used it for awhile now and haven't had one single problem. It seems to be much more stable these days.

---

### Post by louis_nichols on 2007-02-15
> **shanepardue said:**
> Yeah writing to NTFS is beta, but just so you know, I've used it for awhile now and haven't had one single problem. It seems to be much more stable these days.

That certainly is good news! :) I wouldn't recommend it, though. Especially to a noob.

---

### Post by mattjames on 2007-02-15
Many thanks.
Ext2 IFS looks like just what I need.
Just a quick question about NTFS support - is this enabled by default, or do I have to mess with the kernel thing? (I probably don't want to mess with the kernel for a while).

---

### Post by shanepardue on 2007-02-15
It requires installing a driver. it's not enabled by default.  [https://wiki.ubuntu.com/ntfs-3g?highlight=%28ntfs%29](https://wiki.ubuntu.com/ntfs-3g?highlight=%28ntfs%29)

---

### Post by Dunrobin on 2007-02-15
> Write support for NTFS under Linux is here. It's beta, but improving.
How do you set that up?  I'm a long-time Windows user (from 3.1 to XP and everything in between), but I am brand new to Linux and I haven't seen anything so far that would let me write files to my Windows XP partition.

EDIT:  Never mind - someone answered my question while I was typing.  ;)

---

### Post by louis_nichols on 2007-02-15
No, you wouldn't have to recompile or anything. Just to install a package and maybe configure the fstab file to automount if you want. more info [here]("https://wiki.ubuntu.com/ntfs-3g?highlight=%28ntfs%29")

There are other howtos on the forum. just run a search.

---

### Post by mattjames on 2007-02-15
Thanks for the link.
It looks a bit daunting for a noob, but at least its been promoted from beta to release candidate.

---

