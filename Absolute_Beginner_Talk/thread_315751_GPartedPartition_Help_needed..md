---
title: "GParted/Partition Help needed."
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by OneEyedMan on 2006-12-09
Well, it seems I kind of made a rather silly mistake. When setting up my Ubuntu/XP dual-boot I made a total of 4 paritions. An NTFS for the XP-monster (hda1), an ext3 for Ubuntu (hda2), a linux-swap (hda3), and an unused ext3 for storage (hda4). The problem is, I made the main Ubuntu ext3 parition too small (2.5 Gb), and the storage partition, which turned out to be unnecessary, was a 22 Gb monster of unused space.

I tried using GParted to remove /hda4 and reallocate the space to /hda2, and managed to get half there, and now I'm stuck.](*,) 

I have 22 Gb unassigned on my drive, but I can't figure out how to add it to hda2 (my Ubuntu parition). Am I missing something blindingly simple, or did I just shoot myself in the foot?

-J

---

### Post by smile_sunshine on 2006-12-09
um what do they look like - do you have hda3 in between hda2 and the free space??
can you post the output of 

sudo fdisk -l    

? 

:)

---

### Post by OneEyedMan on 2006-12-09
Here's what I got from the fdsik:

******
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6382    51263383+   7  HPFS/NTFS
/dev/hda2            6383        6717     2690887+  83  Linux
/dev/hda3            6718        6849     1060290   82  Linux swap / Solaris

******

So I guess the answer is yes, hda3 (swap) is between hda2 and the free space.

-J

---

### Post by rsambuca on 2006-12-09
Are you using the gParted from within ubuntu, or the gParted liveCD (the latter which I highly recommend)?

---

### Post by OneEyedMan on 2006-12-09
I'm using the Gparted from within Ubuntu. I honestly hadn't given a moment's though to whether there was a gParted Live CD...

-J

---

### Post by Bartender on 2006-12-09
I don't know if I can help you with the biggest problem, but there's no need to make linuxswap as a primary partition.  You can make it as an extended (hda5) partition, saving primary partitions in case you decide to multi-boot or whatever.

I'm assuming you want to leave the Windows partition alone.  Delete the other ones so you have one big unassigned partition behind Windows and start over.  I think the following would work...
  
Make an ext3 (primary) partition for Ubuntu.  That would be hda2.

Make another for storage.  Would it be better to make it vfat so that Windows could also use it?  Also, the storage could be extended rather than a primary partition.  It would be hda3 if primary, hda5 if extended.

Then put swap out at the end.  Swap will be hda5 if you made your storage partition as a primary partition, or hda6 if you already built an extended partition for storage.  I don't remember the details (been a few weeks since I used Parted) but when you create the partition for swap you can assign it as linuxswap and make it extended.

The separate [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") is cool.

---

### Post by smile_sunshine on 2006-12-09
What I would do is delete hda3 and then remake it at the end of the disk, then try adding the rest of the space to hda2.

As rsambuca says I think you would need to use the live cd not change the partition you are in at the moment.

I definately recommend backing the ubuntu partition up first though, just in case.

---

### Post by rsambuca on 2006-12-09
I think to do what you want you will have to download the gParted live CD.  If you are using the gParted program from within ubuntu, you will have problems because your hda2 drive is mounted.

I would recommend this:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by smoker on 2006-12-09
probably the easiest way would be to shrink the windows partition and take up the free space from there.

i too would recommend the separate gparted boot disc.

---

### Post by Brownedwg89 on 2006-12-09
i would suggest deleting your swap, and remaking it at the very end and resize hda2 to use the rest of the space

---

### Post by OneEyedMan on 2006-12-09
Thanks everyone. I downloaded the gParted LiveCD, and I was able to get the free space reallocated to hda2, and move the swap to the back of the drive without a problem. I'm getting some funky warning durign startup that hda4 is not reading properly, which doesn't surprise me, considering it doesn't exist anymore, but I've been able to cancel out of it wihtout any effect. I'll look into that a bit later.

Thanks again!

-J

---

