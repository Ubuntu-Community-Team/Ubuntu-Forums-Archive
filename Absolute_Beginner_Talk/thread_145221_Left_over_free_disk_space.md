---
title: "Left over free disk space"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by Peter Mount on 2006-03-15
Hello

After installing Ubuntu 5.10 onto my hard drive I'd just like to know what the minimum amount of free space is I should keep set aside on the partition for it to run properly.

I have:

Pentium 2-350
448 mg PC100 SDRAM
64 mg Radeon ATI 7000 video card
8.4 gig hdd (for the Linux install)
10 gig hdd (currently for Windows)

Thanks

---

### Post by o_fortuna on 2006-03-15
[QUOTE=Peter Mount]Hello

After installing Ubuntu 5.10 onto my hard drive I'd just like to know what the minimum amount of free space is I should keep set aside on the partition for it to run properly.

I have:

Pentium 2-350
448 mg PC100 SDRAM
64 mg Radeon ATI 7000 video card
8.4 gig hdd (for the Linux install)
10 gig hdd (currently for Windows)

Thanks[/QUOTE]
As with all operating systems, it's usually good to have some free space. Unlike windows, which doesn't have separate space for swap, Linux actually doesn't need that much. A good formula is to always keep at least 10% free space -- so thats like 840MB. This ensures that if you want to create files you won't run into low disk warnings and the like.

---

### Post by Zeroangel on 2006-03-15
It really depends on if you're going to put your /home/username (aka: my documents) folder on a seperate partition.

The minimum you should set aside for an ubuntu install is 4GB for the / (root) partition (this is important if you want to install a lot of programs), and 400+MB for the swap partition. After that the rest is all icing on top of the cake.

If you are worried about HD space, you should make a /home partition, just so that the documents, music, movies, or whatever you use do not end up cannibalizing the temp and folder space that you might need for your programs.

---

