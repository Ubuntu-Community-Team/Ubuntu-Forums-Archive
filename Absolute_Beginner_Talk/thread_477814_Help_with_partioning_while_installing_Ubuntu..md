---
title: "Help with partioning while installing Ubuntu."
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by johnd29 on 2007-06-18
I'm having a problem with the partition part.

This is what I have, and I don't know how to resize my ntfs partition to get some free space:

[http://img379.imageshack.us/img379/7...eenshothk8.png](http://img379.imageshack.us/img379/7...eenshothk8.png)

---

### Post by guardsman85 on 2007-06-18
> **johnd29 said:**
>  
[http://img379.imageshack.us/img379/7...eenshothk8.png](http://img379.imageshack.us/img379/7...eenshothk8.png)

not found.  would you please post again?

EDIT: Perhaps just copying the whole path so it doesn't get truncated or use tinyurl.com.

---

### Post by joe.turion64x2 on 2007-06-18
> **johnd29 said:**
> I'm having a problem with the partition part.

This is what I have, and I don't know how to resize my ntfs partition to get some free space:

[http://img379.imageshack.us/img379/7...eenshothk8.png](http://img379.imageshack.us/img379/7...eenshothk8.png)
The image is no longer available. Anyway, provided you have enough free space in the NTFS partition Gnome Partition Editor should resize it: I always resize NTFS partitions with Gparted to make room for Linux!

Just open Gnome Partition Editor, select the partition, right click, Resize, configure the new size, Apply, and you are done.

Joe.

---

### Post by johnd29 on 2007-06-18
Sorry, got it figured now.

Just to be sure:

swap as: extended partition, and swap.
root as: primary partition and ext3
home as: primary partition and ext3

right?

---

### Post by bren on 2007-06-18
sounds ok

bren

---

### Post by johnd29 on 2007-06-18
swap as extended partition, right??

---

### Post by johnd29 on 2007-06-18
Oops, I meant primary or logical.

---

### Post by guardsman85 on 2007-06-19
I think that as long as those three partitions are the only three partitions on the disk that you should be fine with all of them as primary.  I'm not sure it matters though.

---

