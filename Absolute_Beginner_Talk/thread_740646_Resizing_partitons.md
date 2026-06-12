---
title: "Resizing partitons"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by dreadh3ad on 2008-03-31
I am currently running a dual boot system xp and ubuntu.  I need to shave 15 gigs of free space off the xp partition and add that to ubuntu.  Can this be achieved with Gparted without reinstalling xp?

---

### Post by JoshuaRL on 2008-03-31
Sure, just make sure you defrag and backup XP before.

You do realize that the 15 gigs will be in another filesystem right?  You'll need to reformat before you can add that to Ubuntu.

---

### Post by Oldsoldier2003 on 2008-03-31
> **dreadh3ad said:**
> I am currently running a dual boot system xp and ubuntu.  I need to shave 15 gigs of free space off the xp partition and add that to ubuntu.  Can this be achieved with Gparted without reinstalling xp?
Yes.
first download a [GParted Live CD]("http://gparted-livecd.tuxfamily.org/") 

next boot into xp and scandisk/defrag (and back up your data)
next boot the gparted live cd and resize your windows partition.

If your ubuntu partition and your xp partiton are adjacent you can grow your partition to use up the extra space. If not i would just suggest creating a new partition and mounting it. Shuffling nonadjacent partitions is a royal pain in the but and time consuming.

edit slip of the mouse on glipper I put supergrub instead of gparted lol!

---

### Post by dreadh3ad on 2008-03-31
Is the Gparted live cd good enough?

---

### Post by Oldsoldier2003 on 2008-03-31
> **dreadh3ad said:**
> Is the Gparted live cd good enough?

opps was firing off the post and didnt notice my mouse slipped when i was using glipper! sorry!

---

### Post by dreadh3ad on 2008-03-31
its ok, thanks for your help!

---

### Post by JoshuaRL on 2008-03-31
Don't forget to Thank him, its the little gold star by Quote.

---

