---
title: "Looking on how to remove Windows XP + Solaris 10 and keep Ubuntu."
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Epiphex on 2008-02-11
Okay, so this is the deal, hopefully someone can help me out with it. I've just finished installing Ubuntu, but have been dual booting w/ Solaris 10 and Windows XP for a while now. I'm looking to remove both Solaris 10 and Windows XP from my system but keep Ubuntu. 

If anyone can direct me on how to do this, that'd be great.

---

### Post by emarkd on 2008-02-11
Why not boot the Ubuntu live CD and use gparted to delete the unneeded partitions.  Then you can resize Ubuntu's partition and give it all that newly freed space.  Or you could leave the partitions, reformat them as ext and mount them under Ubuntu somewhere.  If you do it that way, you can even do it from Ubuntu without using the live CD.

---

