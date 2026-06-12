---
title: "Can't resize NTFS (New Compaq Presario V4000T)"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by neko18 on 2006-07-24
I'm not able to resize the main Windows NTFS partition using either GParted itself or the version embedded into the installer. Does anyone have a clue what's going on? I'm trying to install Ubuntu Dapper 6.06. Please see screenshots for more information (they were taken on a LiveCD).

---

### Post by OpsVentus on 2006-07-24
It says it cannot read it so it may contain error's.
You can try to check it under Windows and then try again, with the GParted live cd.

Cheers,
Bart.

---

### Post by Sart on 2006-07-24
If I am not mistaken, Linux cannot write to NTFS, though reads it OK. You'd better try to boot to Windows and resize it from there. I'd recommend something like Partititon Magic 8.0. I used it myself to create Linux Swap and Ext3 volumes under Windows. Then I used LiveCD to boot and install Ubuntu.

---

### Post by neko18 on 2006-07-24
> **OpsVentus said:**
> It says it cannot read it so it may contain error's.
You can try to check it under Windows and then try again, with the GParted live cd.

Cheers,
Bart.
Windows error checker doesn't find anything.

> **Sart said:**
> If I am not mistaken, Linux cannot write to NTFS, though reads it OK. You'd better try to boot to Windows and resize it from there. I'd recommend something like Partititon Magic 8.0. I used it myself to create Linux Swap and Ext3 volumes under Windows. Then I used LiveCD to boot and install Ubuntu.
Linux can resize NTFS partitions, I've done it on another computer (with Ubuntu, too). I'll attempt Parition Magic later though, if it has a free trial.

---

### Post by OpsVentus on 2006-07-25
I don't know if it helps but in this kind of situations I would use the Live cd of GParted.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
This one won't mount anything and let's you adjust your partitions.

Other whish I think trying to copy the data to a different disk and then rearrange the partitions is the fastest way to solve this.

Cheers,
Bart.

---

### Post by mejohnsn on 2006-07-27
If by 'NTFS', you had meant the **filesystem**, you would have been correct: linux cannot write to an NFTS filesystem without the extra help of FUSE, ntfsprogs, ntfs-3g or something of that class. And the Dapper release of Ubuntu has bugs in the versions of FUSE and ntfsprogs on the CD, so that it is difficult or impossible (I am not sure which) to use it as is, especially on a liveCD.

But as others in this thread pointed out, certain tools under Linux can manage NTFS partitions just fine.

---

### Post by molly_001 on 2006-07-27
neko18 --

I have run into this before with a brand new OEM install of Windows XP.  In all cases I have been able to get around it by doing the following:

1) reformat & reinstall Windows XP onto 100% of the hard drive
2) use the Live-CD of GParted (a separate stand-alone GParted CD) to resize that single NTFS partition down to the size you desire
3) use the Alternate Install CD for Ubuntu 6.06 to install Ubuntu

---

### Post by OpsVentus on 2006-07-28
Well if you are going to format the disk why not partition it the right way from the beginning?
This is way better, becauss resizing a partition is a tricky thing to do.

Cheers,
Bart.

---

