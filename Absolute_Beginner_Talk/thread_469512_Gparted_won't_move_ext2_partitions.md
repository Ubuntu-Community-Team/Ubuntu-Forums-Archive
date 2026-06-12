---
title: "Gparted won't move ext2 partitions"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-06-10
I'm trying to reformat my windows partition and add space to the ubuntu one (then reinstall windows, then reinstall grub)

so far, i've got this

47.3 megs of dell utility partition (apparently i need this one) (fat 16)
93.14 gigs of free space
51.23 gigs of ubuntu (ext2)
4.6 gigs of swap (i know this is alot, i didn't know what it was for when i originally installed ubuntu, so i gave it more than enough so that i would never run out)

when i try to move/resize the ext2 partition to make it in front of the free space, it wont let me.

i've checked the "Features" menu, and it says that it is not possible to move ext2 files.


so what do i do?

---

### Post by koshari on 2007-06-10
this is likely due to it being mounted, you may have better luck using a live disk to do it.

---

### Post by ramjet_1953 on 2007-06-10
You can't re-size a mounted partition!

Have you ever tried changing a tyre on a car, while it was being driven? :D

You can either use the live CD, or just download the GParted iso and burn it to a CD (my preference)

Regards,
Roger :cool:

---

### Post by ThinkBuntu on 2007-06-10
Use the LiveCD. Gparted is very, very useful for these things.

---

### Post by Herman on 2007-06-10
I agree with koshari and ramjet_1953, you should download [GParted -- LiveCD]("http://gparted.sourceforge.net/") and burn one of those to disc if you get an .iso or make a USB disk GParted.
GParted on the [GParted -- LiveCD]("http://gparted.sourceforge.net/") is the only GParted that has the features to move a Linux partition or resize it from it's start point. 
The version of GParted that's in the Ubuntu Live CD or even that we can install from the repositories is very old, maybe because it's a lot of work to get it integrated with everything else. Other distros I have checked also have the same old version of GParted, which is over a year old and very outdated. (Version 0.2.5)

Meanwhile new versions of GParted LiveCD have been coming out every few weeks, the current version is 0.3.4-7 now, GParted LiveCD [News]("http://gparted.sourceforge.net/news.php") (19 Mai) Check the features! :)
So if you want to be able to do what you want get [GParted -- LiveCD]("http://gparted.sourceforge.net/").

:D I also like the analogy of changing a tire while the car is still being driven! :D
```
 Have you ever tried changing a tyre on a car, while it was being driven? 
```Cool! Thanks ramjet_1953  , that's a great analogy!  :D


Tyke91, if you use  [GParted -- LiveCD]("http://gparted.sourceforge.net/") you won't need to worry about unmounting things either, it will do everything for you automatically.

Regards, Herman :D

---

### Post by Tyke91 on 2007-06-10
LOL was using a live CD (ubuntu since it comes with gparted)

for some reason it WAS re-mounting the disks tho

---

### Post by STREETURCHINE on 2007-06-10
download the gparted live cd the gparted that comes with the ubuntu live cd does not seem to work right,

there are links in the above posts for the gparted live cd:p

---

