---
title: "Choosing right filesystem"
date: 2005-07-24
forum: Absolute Beginner Talk
---

### Post by skatedawe on 2005-07-24
Hi, i would like som help with choosing the right filesystem for my harddrives.

 I have theese harddrives:

 1. 80GB - Ibm - IDE (p)Ata 133 - 2mb cache
 2. 160GB - Hitatchi - IDE (p)Ata 133 - 8mb Cache
 3. 250GB - LaCie - IDE (p)Ata 133 - (USB 2.0) - [EXTERN] - 8MB cache

 -----

 I think i will use my 80gb IBM to run the system.

 1. 1024 Swap , 70Gb ext3 ?
 2. suggestions ? ( Fat32 :/? )
 3. It is already formatted as Fat32, but will it work to have it with Fat32. I would like to have a filesystem for both win and linux, so i could lend it over to some friends :).

 The problem is that i dont want to lock me up with a filesystem that wont work properly :(, i will have like all my music and stuff on the 2. and 3. so plz help.

 I heard that FAT32 will work for both win and linux, but it is kind of slow?

 Thanks for all kind of suggestions & posts!

---

### Post by Kvark on 2005-07-24
I'd put this on 1 and 2:
swap (ext3) = same amount as RAM, or a bit more.
/ (ext3) = what is needed for system, programs, etc... depends on how much you plan to install.
/home/ (ext3) = everything else.

That could mean for example 1GB swap, 10GB / and 229GB /home/ all ext3.

...and let 3 be one big fat32 partition.

---

### Post by skatedawe on 2005-07-24
Thx, i will do that.

 I think ...  :-)

---

