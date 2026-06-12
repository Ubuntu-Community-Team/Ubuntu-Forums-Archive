---
title: "all partitions locked in Gparted (except swap)"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by shanike on 2007-05-13
i wanted to resize my partitions using GParted, but all my partition except swap are locked... offcourse, you can't adjust a partition while you're using it, but i had an application in windows, which scheduled such actions and executed them during booting into win again..

[IMG]http://img522.imageshack.us/img522/7584/gpartedbu6.png[/IMG]

---

### Post by Martje_001 on 2007-05-13
You have to umount them ;). Are you running from a live-cd?
Right-click --> unmount (or something) to unmount...

---

### Post by heimo on 2007-05-13
Boot from live-cd. I think Ubuntu Live CD also has this by default (needed for install), but here's another choice:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by shanike on 2007-05-14
ok, somehow i get the feeling that GParted is not capable of doing anything useful while running in ubuntu. at least not on my machine.

i'm not thinking about using GParted from ubuntu live cd > i just want to partition my drive, why should i do (in this case, load -almost- complete OS) anything else for that?!? (this is actually a windows syndrome :) )

because of that, i have burned my GParted liveCD. works ok, but i'm curious > i'm sure it's good enough to partition and adjust drives for linux systems etc., but is it the appropriate tool for NTFS/FAT32 systems? or should i use different app for that?

---

### Post by ugm6hr on 2007-05-15
I think the GParted Live CD has the latest version which can handle most functions on NTFS.  It has always been able to handle FAT32.  To check - load GParted LiveCD, then select from menu: GParted -> Features.  This lists all the various filesystems it will detect, and the functions it will perform on them.

Rather unusually, the GParted in the Ubuntu repository is not the latest version (0.2.5 vs 0.3.4-5)

(Please note - I haven't tried GParted to resize NTFS yet myself - but have no reason to suspect it shouldn't do what it says on the tin!)

---

### Post by mcduck on 2007-05-15
Resizing NTFS with gParted is safe, and works just great. Anyway, that's what you do when you install Ubuntu, resizing your windows partitions ;)

And yes, you need to run it from a live-CD, as it's not possible to resize mounted partitions. I can't see any problem in that.

---

