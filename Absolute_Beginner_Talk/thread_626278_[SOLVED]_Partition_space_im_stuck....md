---
title: "[SOLVED] Partition space? im stuck..."
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by siongz on 2007-11-28
Hi... i am trying to reinstall Ubuntu and im stuck at the partitioning section.
I have a 37GB for my windows and 42GB free space...
im trying to install ubuntu within the 42 GB
*but have no idea what to do??? * (wish to do it manually coz screwed up once before >.<)
like how much for each root?
and what about primary and logical??

please help me on this... thx

---

### Post by bluepowder7 on 2007-11-28
i'm not sure if the automatic installer will set up the separate swap space that it needs, but if you just want a simple straightforward install, allocate the whole thing for /root.  it'll put /home and /boot into there as well by default since you're not specifying to put it somewhere else.

if you only have those 2 partitions (37 for win and 42 for linux), then they'll all be primary and you don't need to worry about extended or logical.

you can likely live with the /root (and /home and /boot as part of it) being around 5 gigs for your install and most of the applications you'll put in.  your documents and music that you create or copy are on top of that and could EASILY use up another 100 gigs by the weekend.  might as well keep those on a separate hard drive (external or internal)

---

### Post by meanburrito920 on 2007-11-28
read the article on install partioning at [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing), it really explains a lot.

---

### Post by BlocknBleed on 2007-11-28
Someone on here once told me for an absolute minimum install with a few basics like office and internet programs a 4Gb / root was enough for him. 
That said, my / partition is almost 12Gb full but I have loads of crap that I hope to remove on my next fresh install and upgrade.

---

### Post by bluepowder7 on 2007-11-28
mm, ya, installing games is gonna suck up A LOT of space.  that's why my windows partitions that i use for games are around 50gigs each (2k and xp)

---

### Post by siongz on 2007-11-28
thx for ur replies... jus to be clear... 

so does it mean i would create:
5GB ext3 mounted on "/"
1GB ext3 used as "swap" mounted on???
the rest ext3 "mounted on "/home"

and what is /root btw... (sry for asking such an idiotic question)

---

### Post by bluepowder7 on 2007-11-28
yup, that would work (if you want to separate /home from /root).   the ratios look good too (i assume you have 1gig of ram on your PC)

only two comments, and they're about swap.  first, it's not ext3, it's a separate file system - make sure to set it up as a linux-swap and NOT ext3.  you'll see it as one of the file systems available (along with FAT, NTFS, JFS, Reiser, and other stuff).  two, i tend to put swap at the very end, which i assume is on the outside of the disk, which i assume is the fastest part of the disk.  i could be wrong on all those, but that's just how i do it.  also makes it easier to resize the other partitions later on cuz swap is RARELY gonna need to be resized - so i cram it right on the outside where it doesn't get in the way of anything.



/root is the main location for your linux install.  everything else is 'attached' to /root, even if it's in a separate partition.  it's kind of like the C:\ of windows.

---

### Post by BlocknBleed on 2007-11-28
> **siongz said:**
> 

and what is /root btw... (sry for asking such an idiotic question)

sorry for the confusion. by "/ root" I just meant " / ".

5Gb / is plenty to play around for a while but you won't be installing a pile of games or other software. It's trial and error. I installed about 3 times before I found what worked for me. Luckily it only really takes about 10 minutes to partition and install when you don't have anything of value yet saved so its not a big deal to have to do it again.

---

### Post by siongz on 2007-11-28
thx a lot bluepowder... really cleared some of my doubts...

---

### Post by CatKiller on 2007-11-29
> **bluepowder7 said:**
> /root is the main location for your linux install.  everything else is 'attached' to /root, even if it's in a separate partition.  it's kind of like the C:\ of windows.

Actually, this is a description of **/**, which is also sometimes **called** root.

**/root** is the Home folder of the **root user**, which is something else entirely.

---

### Post by meanburrito920 on 2007-11-29
btw, its always good to defrag the windows partition before installing.

---

