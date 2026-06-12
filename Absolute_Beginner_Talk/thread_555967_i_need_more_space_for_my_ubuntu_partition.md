---
title: "i need more space for my ubuntu partition?"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by shortybookit on 2007-09-20
a few weeks back i was watching some youtub videos on ubuntu so you guessed i installed a dual boot with XP... after a crap load of grey hairs with the terminal window i am begining to love ubuntu and am booting to it more than windows.  But to do the complete switch from xp to ubuntu i need more space on my ubuntu partition WITHOUT deleting what i already have on either of my partitions is there a simple way to take 15gigs from xp and give to ubuntu again with out deleting any info on either partition

---

### Post by doronb2 on 2007-09-20
you can install Partition magic on your windows partition and this program can do what you want.

---

### Post by benx009 on 2007-09-20
i would recommend gparted application included on the ubuntu live cd (you would want to use a live session to do this, so that your hard drive is not in use).  however, i would seriously suggest that you check out the [howto on resizing partitions]("http://gparted.sourceforge.net/larry/resize/resizing.htm") unless you know absolutely what you're doing.

---

### Post by arkara on 2007-09-20
or use a gnome partition editor
you can download it from add/remove
live cd has it already if you want to boot from there

anyway...
you will need to resize the ntfs partition first
and then add the unallocated space to  the ubuntu partition by resizing that too
:D

---

### Post by rsambuca on 2007-09-20
Backup everything first.
Defragment the XP drive.
Defragment the XP drive.
Defragment the XP drive.
Use the [gParted liveCD]("http://gparted.sourceforge.net/") and shrink the XP partition
Expand the ubuntu partition.

---

### Post by bodhi.zazen on 2007-09-20
> **rsambuca said:**
> Backup everything first.
Defragment the XP drive.
Defragment the XP drive.
Defragment the XP drive.
Use the [gParted liveCD]("http://gparted.sourceforge.net/") and shrink the XP partition
Expand the ubuntu partition.

Make it so :twisted:

---

