---
title: "Did I accidentally format my hard drive?"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Famous Mortimer on 2007-12-30
I've just installed, so apologies if this has been dealt with a million times. I've found the non-system hard drive, with all my music on it, but the one that had / has Windows on it, which also had my torrents and a bunch of other stuff, appears to have rather more free space on it than when I installed Linux this morning.

So did I press the wrong thing while installing Ubuntu? Any way of getting those files back?

---

### Post by LaRoza on 2007-12-30
Boot into Ubuntu, run:

```

sudo fdisk -l

```

(That is a lowercase L)

Post the results here.

---

### Post by Liolikas on 2007-12-30
If you formated your partition with good files so your files are lost. sry.

You can try:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
But formating with ext3 wipes everything carefully with almost no chances to get something back.

Just this is big lesson to be careful and double-check everything when you alter your partitions.

---

### Post by LaRoza on 2007-12-30
> **Liolikas said:**
> 
Just this is big lesson to be careful and double-check everything when you alter your partitions.

Wait for the results of the command....

---

### Post by Famous Mortimer on 2007-12-30
Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0cab0caa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19363   155533266   83  Linux
/dev/sda2           19364       19929     4546395    5  Extended
/dev/sda5           19364       19929     4546363+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x54ac2310

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS


My own stupid fault, I know. You'll be damn sure I'm going to have a steep learning curve with this thing. It's the 169 GB drive that has the system on it, the other one is music.

---

### Post by LaRoza on 2007-12-30
> **Famous Mortimer said:**
> Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0cab0caa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19363   155533266   83  Linux
/dev/sda2           19364       19929     4546395    5  Extended
/dev/sda5           19364       19929     4546363+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x54ac2310

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS


My own stupid fault, I know. You'll be damn sure I'm going to have a steep learning curve with this thing.

I have bad news. You overwrote the NTFS partitions during the install, you must have chosen the first option. 

Don't blame Ubuntu, but don't be too hard on yourself. For someone unused to installing OS's, it is easy to make a mistake.

The only good news I have is that I am sure with a little work, you'll find Ubuntu a good replacement, and I am sure you'll find Deluge suitable for getting the torrents back.

(You can try the Post #3 link to the system rescue CD, but don't get your hopes up too far)

---

### Post by Famous Mortimer on 2007-12-30
It's fine, I suppose I'm due at least one big mistake while making the changeover. On the plus side, I figured out how to get Rhythmbox to play mp3s (all on my own :) ) so it's a day of swings and roundabouts. If I'd lost my mp3s, I'd be off round Ubuntu's offices to burn them down :)

---

### Post by LaRoza on 2007-12-30
> **Famous Mortimer said:**
> It's fine, I suppose I'm due at least one big mistake while making the changeover. On the plus side, I figured out how to get Rhythmbox to play mp3s (all on my own :) ) so it's a day of swings and roundabouts. If I'd lost my mp3s, I'd be off round Ubuntu's offices to burn them down :)

Remember to back up!

I made mistakes too, although I admit I never lost data before.

If you need guides: 

[http://www.psychocats.net/](http://www.psychocats.net/)

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

And if that fails, the forum.

---

### Post by Famous Mortimer on 2007-12-30
Again, many thanks, and I look forward to asking many similar idiot's questions in my early weeks of using Linux.

---

### Post by LaRoza on 2007-12-30
> **Famous Mortimer said:**
> Again, many thanks, and I look forward to asking many similar idiot's questions in my early weeks of using Linux.

Hopefully not too similiar :)

Soon, you will be answering questions too.

---

