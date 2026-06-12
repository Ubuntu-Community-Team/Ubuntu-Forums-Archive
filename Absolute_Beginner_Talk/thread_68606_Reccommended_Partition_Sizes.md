---
title: "Reccommended Partition Sizes"
date: 2005-09-23
forum: Absolute Beginner Talk
---

### Post by Petawa on 2005-09-23
I recently bought a Compaq V2310 laptop. The fact that I want to take advantage of the 64-bit Turion made me want to switch to Linux. My brother pointed me to Ubuntu, so here I am. Its not that I don't like Windows XP, I've never had a problem with it. Just I got bored and I want something I can fiddle with a bit more.

Anyway, this laptop has a 80GB HD. I'm going to set up a dual-boot, and I'm going to update XP to 64-bit Vista when its available. I was wondering the most effective usage of the space.

Reading [this thread](http://ubuntuforums.org/showthread.php?t=60883), I've come up with the following rough divisions:

WinXP (NTFS) 25GB
/ (root) 15 GB
1 GB swap
40 FAT32 Shared
/home ??

Basically, I want my windows partition to hold a couple games and basic productivity programs, that's it. For Linux, I'm probably not going to install much other than the default programs, and maybe a FOSS FPS. I'd like the FAT32 to be as large as possible, its going to hold my MP3s and Family Guy episodes. I also heard that a separate /home partition will make upgrading easier, but I have no idea how large I should set it (as I said, the FAT32 will hold all misc files).

Any help would be appreciated, I have until 5.10 comes out to decide anyway.

Thanks,
Peter

---

### Post by SilentCacophony on 2005-09-23
Hello. You can really set things up in many different ways. Personally, I just use about 5 GB for /, 1 GB for swap, and I store files on other mounted partitions. With my 20 and 10 GB drives looking like so:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             4.9G  2.2G  2.5G  47% / <-Ubuntu Breezy
/dev/hda1             2.4G  523M  1.9G  22% /media/hda1 <- Windows 98
/dev/hda2             3.0G   65M  2.7G   3% /media/hda2 <- Distro of the week space
/dev/hda5             3.9G   66M  3.7G   2% /media/hda5 <- File storage for Breezy
/dev/hda6             3.9G   65M  3.7G   2% /media/hda6 <- File storage for whatever
/dev/hdb1             9.6G  2.8G  6.8G  30% /media/hdb1 <- vfat shared storage

```

The swap is on hda7.

I'd go no less than 3 GB for root, unless you're doing a minimal server install. If you made /home on a seperate partition and run out of space, you can always mount another partition and move some files there.

---

### Post by aysiu on 2005-09-23
I think your partitioning plan looks good. You may not need 25 GB for Windows or 15 GB for /. I'd shrink Windows down to about 10 GB and root also down to about 10 GB, leaving you a larger FAT32 partition to share files on. And the /home partition can be as little as 1 GB if it's going to hold just your settings and preferences (I'm assuming all your large files would live on the FAT32 partition).

---

### Post by matthew on 2005-09-23
Just for the sake of comparison you might appreciate this thread:
[http://www.ubuntuforums.org/showthread.php?t=48561](http://www.ubuntuforums.org/showthread.php?t=48561)

---

