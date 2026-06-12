---
title: "partition resizing attempt, confusion re 'mounting' drives"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by karinne on 2006-10-17
Hi all, 
New to Ubuntu, not totally new to Unix (but no expert either). I spend most of my time in XP, but have just installed ubuntu on my home system and so far I absolutely love it. 
My question- I want to resize my hdd partitions. I have my ubuntu one set larger than I need, and I would prefer to re-enlarge my XP partition as I do a lot of large-file media stuff and a lot of cpu intensive number crunching and 3D modeling, so (so far at least) the XP partition should be the largest one. 
I have GParted, and know how to get into it and can see the drives. here's what is there:


/dev/sda1       ntfs      (size)76.13GB  (used)25.79 GB (unused)50.34 GB      (flag) boot
/dev/sda2        ext3     (size)155.51GB     (used)4.75GB     (unused)150 GB
/dev/sda3      extended    (size)1.25GB      ---        ----
/dev.sda5     linux-swap   (size)1.25GB       ---       ----

my questions about this :  
what are the extended and linux-swap partitions? what's there, etc. 

All of the command mouuse buttons are greyed out- the 'new', 'resize-move', etc.  Except for "unmount", which I am unsure about. What does that command do?  How do I go about resizing them the way I want to? 

I have many, many more Ubuntu questions- program compatibility, etc, but I'll try to figure them out before posting a bunch of new threads.  Thanks!

regards, 
karinne

---

### Post by theboomboomcars on 2006-10-17
You cannot resize a mounted partition, you'll have to unmount it first.  Although I am not sure if you can resize a ntfs partition from Ubuntu.

---

### Post by karinne on 2006-10-17
so what would happen if I unmounted it? How does that afffect that partition, the data on it, etc. (exactly what does mounting and unmounting do?)
What if I shrank down the ext3 partition? would that grow the ntfs partition by default? I really don't know how this works, obviously. Thanks for your help.

---

### Post by Sef on 2006-10-17
> so what would happen if I unmounted it?

If you boot into GParted, you harddrive is unmounted.

> How does that afffect that partition, the data on it, etc. (exactly what does mounting and unmounting do?)

Since your harddrive will be unmounted, there will be no problems with partitioning.

Mounted to simplify means the harddrive is running.  Unmounted means it is not running.

> What if I shrank down the ext3 partition? would that grow the ntfs partition by default?

The NTFS would not grow by default.  With the latest GParted - 0.3.1 - you can shrink or increase the size of a partition from either the beginning or the end.

Read [GParted's]("http://gparted.sourceforge.net/larry/resize/resizing.htm") How to Resize Partition, first.

---

### Post by karinne on 2006-10-18
thanks for the answers. I have read that; still, even with any one of the partitions highlighted, the commands in the dropdown menu, as well as the button commands, are still greyed out. I have read that this may be b/c I have gparted from the Ubuntu liveCD, not the gparted liveCD. I will try this again later by taking gparted as .iso and burning to cd and installing that way; maybe then it will work.

---

