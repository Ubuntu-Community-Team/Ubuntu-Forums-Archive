---
title: "Remove XP from drive?"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by not_yet on 2008-04-11
Hi,

I have Hardy on half my drive and xp on the other half. i would like to remove xp, and give Hardy the whole drive. whats the best (safest) way to do that?

thanks

---

### Post by Schendje on 2008-04-11
You can probably use the [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php").

However, I wasn't sure how exactly to do it myself (I'm still new to Ubuntu) so I just wiped the entire disk and reinstalled Ubuntu. I'd still give GParted a look if I were you though. Hope it helps. :)

---

### Post by smurphy_it on 2008-04-11
You can just boot off of the Ubuntu live CD.  Run gparted (Partition Editor) and delete the windows partition.  Afterwards, resize your partitions for linux (or create additional mount points).

So if you use a /home partition, you can always increase the size of that one if you so desire.

---

### Post by njparton on 2008-04-11
You probably won't need to boot from the live CD if you haven't mounted the windows partition in ubuntu.

---

### Post by bumanie on 2008-04-11
There are a number of ways you could go about this. Assuming you don't want to reinstall (as above), gparted live cd would be a good way to go. It can format most file system types and can also copy whole partitions. You can't copy a large partition to a smaller partition. Therefore, if the ubuntu partition is smaller than the windows partition, you should be able to format the windows partition with ext3 and then copy ubuntu to that partition. You would then resize the ubuntu partition to take the whole drive. Ubuntu should still boot as long as the partition is labeled with a UUID number (which it should be) because this is what grub reads to decide where to boot from. If for some reason, your computer gets a grub error, grub should be able to be reinstalled via the ubuntu live cd. I guess you are aware that hardy heron is still in the beta stage of development and that its stability can't be guaranteed. Get gparted live cd here [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Is this 100% safe - no. Partitioning etc can go wrong. It would be advisable to backup /home (and anything else important) before you start.

---

### Post by zvacet on 2008-04-11
@** njparton**


> You probably won't need to boot from the live CD if you haven't mounted the windows partition in ubuntu.

But how will he add free space to the mounted partition?

---

### Post by njparton on 2008-04-11
> **zvacet said:**
> @** njparton**




But how will he add free space to the mounted partition?

True

---

### Post by SlappyPappy on 2008-04-11
The Partition Editor on the LiveCD should do the trick. I used it to help me clone my install from a small HD to a larger one and it worked perfectly resizing.

Good luck.

---

### Post by not_yet on 2008-04-11
thanks all:)

used the gparted live cd / deleted the ntfs partition, and resized

worked great

cheers

---

### Post by stchman on 2008-04-11
> **not_yet said:**
> Hi,

I have Hardy on half my drive and xp on the other half. i would like to remove xp, and give Hardy the whole drive. whats the best (safest) way to do that?

thanks

Boot the LiveCD, select install, when the disk partitioner comes up tell it to use the ENTIRE disc.  This will wipe the hdd and install Ubuntu.

Be sure you want to do this, you will not be able to get back data after you have erased it all.

---

