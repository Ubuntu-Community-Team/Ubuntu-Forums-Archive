---
title: "Deleting Ubuntu Partition"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by dexwiz on 2007-07-18
I and experimenting with Ubuntu and I am afraid I royally messed it up and would just like to reset that partition. I also have an instance of XP installed and don't really want to loose the data on it. Can someone give me a way to remove it cleanly without leaving a swap partition or anything? Thank.

---

### Post by Koybe on 2007-07-18
Boot normaly your Windows XP OS, go the the disk manager and remove any parition not being ntfs or fat one (which are windows partition). They should appear after your windows parition.

Then if you really don't even want to reinstalle any linux system, you'll have to clear your mbr to make the dual boot (grub) disappear. Just type 'fdisk /mbr' in a dos console.

---

### Post by sab0403 on 2007-07-18
Also you'll have to resize your partitions, in case you want to use the space you just cleared.

The easiest way to do that is with GParted, and the Ubuntu LiveCD. If you have it available, just read [this thread]("http://ubuntuforums.org/showthread.php?t=493631&highlight=ubuntu+corrupted+windows+gparted") and you'll find a how-to (around page 5 or 6, IIRC).

Hope this helps. :popcorn:

---

