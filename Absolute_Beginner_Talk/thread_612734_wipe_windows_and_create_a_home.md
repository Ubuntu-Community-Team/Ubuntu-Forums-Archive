---
title: "wipe windows and create a /home?"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by natehatewindows on 2007-11-14
ok so my plans are to wipe my vista partition and i hope i can create a separate /home partition without doing a fresh install of gusty (i dont want to have to get my winmodem to work again).

so if anyone could help me with step by steps i would love it.

here is a screen shot of gparted.

im also playing with the idea to dual boot with mandriva or SUSE....or some other linux distro....any ideas? 

thanks!

---

### Post by philinux on 2007-11-14
You need to follow these 

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

instructions

---

### Post by natehatewindows on 2007-11-14
ok so i looked at the link. it is possible to just wipe my windows partition from my working gusty install and create the new /home and then boot the live cd and edit the file? also when i wipe windows will i need to move, rename or change any files or partitions other than my grub/menu.lst (to not have the option of booting windows)?

---

### Post by philinux on 2007-11-14
Yes using gparted from the live cd you can reformat the windows partition to ext3 and make it your home partition.

The instructions are pretty good from psychocats. i recently did this. when I came to reinstall gutsy, the upgrade didn't work, it was a doddle.

---

### Post by natehatewindows on 2007-11-14
if you look at the image i attached ou can see now my ubuntu partition is 22 gigs, should i shrink that if im going to make  80 gig /home? or can i shrink it?

---

### Post by hogwartsnigel on 2007-11-14
You may want to down load the super grub disc just in case...I've just finished deleting windows partitions from my system and all well.

Nigel

Good luck

---

### Post by Inxsible on 2007-11-14
If you already have a separate home partition, you can simply merge the vista partition into the home drive (after formatting of course)

you dont need an 80 GB home partition. Hell you don't even need a 22GB root. This is what I have, YMMV
9 GB root
20 GB home (of which only ~400 MB is used -- so go figure :) )
80GB shared data (movies,music,pictures etc)
25GB Vista (the OS -- can you imagine it takes bloody 21 GB)
15 GB Windows Data (some apps that dont work in Linux like a few games, turbotax etc)

---

### Post by Inxsible on 2007-11-14
you also have a lot of space wasted in between , i see a 1 mb unallocated space also a 6mb. Then there is a 1.5GB ntfs drive which has errors i think.

Try creating logical partitions to utilize your drive space. To read more about partitioning, follow this [link]("http://ubuntuforums.org/www.psychocats.net/ubuntu/partitioning")

---

### Post by natehatewindows on 2007-11-14
ok so i guess i need to shirnk my root down to maybe about 8 gigs, create a /home thats 10 gigs (is the enough?) and then use the rest for a shared. how would i do this? i can merge the unallocated when i creat on of the partitions right?

---

### Post by Inxsible on 2007-11-14
> **natehatewindows said:**
> ok so i guess i need to shirnk my root down to maybe about 8 gigs, create a /home thats 10 gigs (is the enough?) and then use the rest for a shared. how would i do this? i can merge the unallocated when i creat on of the partitions right?
Correct. The unallocated spaces can be merged. Make the /home about 15-20 gigs, just in case.

---

### Post by natehatewindows on 2007-11-15
in doing all doing all of this will my sda# change on my partitions? if so what file(s) do i need to change and how?

---

### Post by hyper_ch on 2007-11-15
and if you wipe it, you maybe required to reinstall grub.

---

