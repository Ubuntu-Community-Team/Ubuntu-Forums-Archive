---
title: "Help!"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Geek33 on 2007-03-06
I finished installing Ubuntu, yay! :D

I set up the partitions for a dual boot, only problem is, GRUB doesn't load when I turn on my computer, and Windows XP starts, then goes to the blue screen of death. :P

At this point I'm ready to say screw windows, since I backed up allllllll my data and the only things in Windows I even need to use would be Mathematica or World of Warcraft, and I can play WoW with WINE.

So my question is, how can I make GRUB installed so it comes up at computer startup? :\ I serached the Live CD for anything GRUB related but it finds no results, so I suspect it didnt' actually put GRUB on..wherever it puts it.

Hoping for a reply! :D

---

### Post by Amenemhet on 2007-03-06
Sounds like you didnt actually do anything. We need more info...but if all you get is the blue screen of death something aint right....try running the live cd, and see if you actually have anything first off, if you can run the live cd, go to a terminal window and type
fdsk -l
this will tell you what partitions you have, and if you see nothing, you have nothing!
Regardless, if you can run the cd, do so and install away....I'll be awaitin...

---

### Post by maniacmusician on 2007-03-06
If you don't care about windows, you may as well wipe the whole disk and do a complete reinstall, foregoing any dual-boot issues.

---

### Post by Geek33 on 2007-03-06
Loaded up the live CD, so here's the output:

root@ubuntu:/boot# fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       16900   135749218+   7  HPFS/NTFS
/dev/sda2           16901       17410     4096575   82  Linux swap / Solaris
/dev/sda3           17411       18685    10241437+  83  Linux

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19451   156240126    7  HPFS/NTFS
root@ubuntu:/boot# 


The sdb1 is a drive connected in a RAID array with me sda1, I couldn't really get that working too well but it didn't seem to impact anything. :\

Edit - By "working too well" I mean having Linux install on both at the same time, I just left sdb1 alone *shrug*

---

### Post by Amenemhet on 2007-03-06
> **maniacmusician said:**
> If you don't care about windows, you may as well wipe the whole disk and do a complete reinstall, foregoing any dual-boot issues.

Listen to the song man me says....always better starting afresh

---

### Post by Geek33 on 2007-03-06
I went into GParted and did manage flags on my /dev/sda3 of which it says 285.33 MBs are being used, I notice there's a ton of checkboxes, should I check boot or something? :S

---

### Post by Geek33 on 2007-03-06
> **Amenemhet said:**
> Listen to the song man me says....always better starting afresh

lol, aight. :P

So what are the steps to completely wipe the HD and install? Just go thru the installer again but this time have it format the huge ntfs partition, or delete it? <_< There's probably a guide somewhere isn't there lol.

---

### Post by maniacmusician on 2007-03-06
When going through the installer, just choose the first option for partitioning. If I recall correctly, it's something like "Erase entire drive [name of drive] and use Free space". Something like that, anyways. Basically  you want to wipe everything and start anew.

---

### Post by Geek33 on 2007-03-06
Aight I will try that. :) Thank you very much and if I have any more Q's I'll be sure to post hehe, I appreciate everyone being so nice. :D

---

### Post by maniacmusician on 2007-03-06
> **Geek33 said:**
> Aight I will try that. :) Thank you very much and if I have any more Q's I'll be sure to post hehe, I appreciate everyone being so nice. :D
Yes, Ubuntu Linux has been known to alter people's personalities and give them sunny dispositions. Rumors say that it also reduces inhibitions, letting people have a hell of a good time :)

---

### Post by Geek33 on 2007-03-06
Hmm at the BIOS it says 'Error loading operating system' :(

---

