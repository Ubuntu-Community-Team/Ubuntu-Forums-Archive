---
title: "Need some help to install ubuntu"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by kiwiz on 2006-07-15
:confused: 
Hi, i need some help to intsall ubuntu.

I was thinking of making 4 partitions; root, boot, swap and home.
I am planning to intall programs on home.

First of all i don't know what filesystems i should use on my partitions and i don't know what partitions that should be primary partitions and logical (i guess root needs to be primary).

uhm, oh i already have winxp installed if that will make any difference.

Thanks!

---

### Post by alecjw on 2006-07-15
I reccomentd that you install it with defaults, wiping your hard drive and making boot and swap automatically. Then, shrink root and make home and the other one. Then make the root and home partitions. boot will automatically be fromatted in ext2 and swap in linux-swap. If you have a fast system, format root and home in ext3. Otherwise, use ext2.

---

### Post by kiwiz on 2006-07-15
Well i left some unallocated space to install linux on. I still want my winxp. 
So i was thinking to format the partitions by using the unallocated space, but i dont know what type of partitions i should use (primary or logical) and what filesystem.

---

### Post by XPuntu on 2006-07-15
The best thing I've seen is this:

[http://www.psychocats.net/ubuntu/partitioning.html]("http://www.psychocats.net/ubuntu/partitioning.html")

This gives you an idea what partitions you should set up. The link on how to partition:

[http://www.psychocats.net/ubuntu/installing.html]("http://www.psychocats.net/ubuntu/installing.html")

I've been on Ubuntu now for three days. I found these two links easy to follow.

Good Luck.

PS. If you have a fast system, I recommend setting up your /home as ext3 and installing the FS drive program listed in the first link. Works like a charm!:-D

---

### Post by kiwiz on 2006-07-15
Thanks very much :) i will look on the links you posted.

---

