---
title: "Corrupted partition with Ubuntu - Blocks?"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by deadimp on 2007-01-22
I've installed Ubuntu 6.10 on my hard drive as a dual boot, paired with WinXP.
Recently, I've hassled with my hard drive after corrupting the partition table (and not backing it up - every dumb-arse's mistake), and managed to restore it a day ago. GRUB is working, and now I know that Windows is working fine and all.
However, Ubuntu no longer boots correct, and complains on startup that something's wrong with my file system (I don't disbelieve this either). Prior to this, it states that the file system says its partition has 5168913 blocks, and that the partition's physical alotment [spelling] is 5166905 blocks. Obviously, that could be a problem since the expected is larger than the phsical.
When I'm in the maintainence shell, I'm able to browse my basic directories (I'm not going to 'manually' go through with it using fsck), though I haven't tried to really browse through the directories.

Question is, what type of blocks is this error referring to? Hard drive-specific blocks (analogous to sectors?), or file system-specific blocks?
On several sites that I've searched, I've received different definitions, and in one [article](http://www.cyberciti.biz/tips/determine-block-size-on-hard-disk-quota.html), someone made a comment that it was ambiguous between f.s. blocks and h.d. blocks.

I pose this mainly for curiosity, since I'm probably just going to reinstall Ubuntu to clear up my swap partition too.

---

### Post by Sef on 2007-01-22
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").   It could fix your problem without having to reinstall Ubuntu.

---

### Post by deadimp on 2007-01-22
Thanks!
Ran into a slight problem with Test Disk though: When I set it to recover my partitions (using Windows), it got the NTFS and ext3 ones all right, however, I had it recover only the Linux partition, thus the Windows partition was removed, and the drive was no longer bootable.
To remedy this, I booted with Live CD, copied the settings from a previous sfdisk dump on Windows, created a new dump, copied the settings for Linux, combined them in a file, and forced sfdisk to read it (I have some experience in doing this now).
The thing I'm running into now, is that I can no longer edit the partitions with gparted (it has the little lock icon next to both partitions - not sure what exactly that entails) - though it may be 'cause I'm using Linux on that drive right now...
Is there a way to have gparted to allow me to edit my partitions while running on them?

---

### Post by louieb on 2007-01-22
When a partition is mounted,  the lock icon  shows up next to it. When running from the hard drive you have to mount the partition with the / (aka root) directory. The easiest way is to use the GParted Live CD.

---

