---
title: "Resize partitions?"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by toykilla on 2006-08-16
I setup my system to dual boot expecting to need to use windows XP quite often, but that is no longer the case. So far I have been able to do MOST of what I need inside ubuntu. I would like to resize my partitions to either have ONLY ubuntu on the drive, or make the XP partition very small.

Currently:

<!---------------XP (50gig)---------------!><!----U (20gig)----!>

Want:

<!-------------------------U (70gig)---------------------------!>

Or:

<!---XP (10gig)---!><!----------------U (60gig)----------------!>


Can this be done without reinstalling? I would rather not loose all my customizations and such.

---

### Post by wjp.reg on 2006-08-16
Make sure you defrag and backup important Windows files and then use gparted to shrink the windows partition and grow your linux partition(s).

I like using the gparted bootable CD for this as you can't perform these tasks if you have already mounted the windows/linux partitions.

You can get gparted CD here [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828")

bon chance mon ami!

---

### Post by kebes on 2006-08-16
If you have the Ubuntu 6.06 install CD, then gparted is already there. Just boot up into the LiveCD session, and run gparted. This will let you resize your partitions. As always, backup first.

---

### Post by daou on 2006-08-16
GParted uses ntfsresize which is a safe way to resize NTFS partitions. But any true adherent to Murphy's law will always back up. ;)

---

