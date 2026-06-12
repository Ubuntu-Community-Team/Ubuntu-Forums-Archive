---
title: "Resize Partitions on Dual Boot system with GParted, will it work with my system?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by KyleBrandt on 2007-07-07
I am dual booting F Fawn and Windows XP, I want to shrink my Windows partition (/dev/hda1, NTFS) and enlarge my F Fawn partition (/dev/hda3, Ext3).  I use Grub to dual boot.  Will the Gparted live cd do this? and if so will it break any of the Partitions, installations, mbr or Grub? Thanks...

fdisk -l output:

```

/dev/hda1   *           1        5874    47182873+   7  HPFS/NTFS
/dev/hda2            5875        5998      996030   82  Linux swap / Solaris
/dev/hda3            5999        7296    10426185   83  Linux

```

---

### Post by annda on 2007-07-07
as long as it's xp and not vista, you will be fine with resizing. the only thing is that you have swap before ext3. you will need to delete it, shrink ntfs, create swap as hda2 again (at the beginning of freed space), and then expand ext3. if the mountpoints change (say, ubuntu root becomes hda2), you will have problems booting and you will have to reinstall grub using the live cd. just in case, a guide how to accomplish that easily:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

BUT as always: defragment under windows and back up/burn the most important documents you have on both partitions first!

---

### Post by jimbob on 2007-07-07
It can be done fairly simply if you have the Gparted stand-alone CD.

If I was you I would shrink the NTFS partition down to the point where you have enough space to hold the entire Linux partition then move the Linux partition into that space.

Then you can grow the end of the Linux partition as large as you want it out to the very end of the disk if desired.

Delete the swap partition and recreate it where you want after you are all done.

Post a screen shot of the Gparted GUI if you can.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by KyleBrandt on 2007-07-07
Went smoothly, didn't have to delete the Swap, just moved it over.  fdisk -l now looks like:

```
/dev/hda1   *           1        1436    11534638+   7  HPFS/NTFS
/dev/hda2            1437        1560      996030   82  Linux swap / Solaris
/dev/hda3            1561        7296    46074420   83  Linux
```

The NTFS shrink stage, and the moving of the swap partition didn't take much time.  However, the moving and extending of the ext3 partition took an hour, the original size was about 9 Gigs. I wonder if it wouldn't have been faster to have imaged everything with partimage, wiped the partition table, and just restored each partition with partimage?  Thanks for your help!

---

