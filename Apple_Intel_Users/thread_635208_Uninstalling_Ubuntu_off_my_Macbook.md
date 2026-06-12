---
title: "Uninstalling Ubuntu off my Macbook"
date: 2007-12-08
forum: Apple Intel Users
---

### Post by UniverseA7X on 2007-12-08
Well, having only a 60GB hard drive, and lots of music and iLife files that take up enormous amount of space, I would like to repartition my HD to only Mac OS X. However, I can't seem to use Boot Camp to repartition. Can I use Disk Utility, or another way without completely having to reinstall OS X?

Any help is appreciated. 



Brandon

---

### Post by khurrum1990 on 2007-12-08
Have u tried the GParted live cd? You can use that to resize ur hard disks.

---

### Post by tiiim on 2007-12-08
> **UniverseA7X said:**
> Well, having only a 60GB hard drive, and lots of music and iLife files that take up enormous amount of space, I would like to repartition my HD to only Mac OS X. However, I can't seem to use Boot Camp to repartition. Can I use Disk Utility, or another way without completely having to reinstall OS X?

Any help is appreciated. 



Brandon

If you have 10.5 its simple.

Log onto live cd, run gparted from terminal and delete ubuntu so its just free space.
Once you just have os x and free space boot back into into 10.5
Open up disk utility and there is a tab there for partitions or something like that.. you see your hard disk with os X and a lot of free space, simply drag your os x partition to cover the whole disk and then apply, 10.5 will extend the partition on the fly.:)

---

### Post by cyberdork33 on 2007-12-09
> **tiiim said:**
> If you have 10.5 its simple.

Log onto live cd, run gparted from terminal and delete ubuntu so its just free space.
Once you just have os x and free space boot back into into 10.5
Open up disk utility and there is a tab there for partitions or something like that.. you see your hard disk with os X and a lot of free space, simply drag your os x partition to cover the whole disk and then apply, 10.5 will extend the partition on the fly.:)

or you can just use Disk Utility entirely.... select the Ubuntu partition (s) and click the minus button to remove it.

---

