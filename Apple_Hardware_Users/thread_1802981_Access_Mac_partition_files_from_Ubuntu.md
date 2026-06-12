---
title: "Access Mac partition files from Ubuntu"
date: 2011-07-12
forum: Apple Hardware Users
---

### Post by Jalaska13 on 2011-07-12
I'm dual-booting Mac OS X 10.6 (soon to be 10.7 :D), and I'd like to access files on my Mac partition from my Ubuntu system.  I intentionally set the same username and password for my Ubuntu system as is set for my Mac system so that I'd be able to access files in both partitions from both OSs.  However, I was trying to import my music into Rhythmbox and it said I didn't have permissions to access ~/Music (in OS X partition).

---

### Post by srs5694 on 2011-07-12
Permissions on both HFS+ and Linux filesystems are not controlled by usernames, but by user ID (UID) numbers. Ubuntu creates accounts with UID numbers beginning at 1000 by default, whereas OS X uses 501 as its first UID number. To simplify sharing files between the two OSes in a dual-boot configuration, the simplest approach is to synchronize your UIDs -- not necessarily your usernames -- across the two OSes. This can be done in Ubuntu with tools like usermod, or probably with GUI equivalents (but I'm not as familiar with them). See my and others' posts in [this thread](http://ubuntuforums.org/showthread.php?t=1595206) for more details.

One more caveat, though: OS X uses journaled HFS+ by default, and unless you use the "force" mount option, Linux will only mount journaled HFS+ volumes read-only. Thus, you'll be able to read, but not write, files on an HFS+ volume from Linux, even when you use sudo. This may be adequate for many purposes, but for greatest flexibility (read/write from both OSes), you'll need to either use the "force" option (which is not recommended in the HFS+ driver documentation, and I especially don't recommend it on an OS X boot partition) or use another filesystem on a separate shared-data partition. The *non*-journaled version of HFS+ seems to work pretty well in Linux and so may be a good choice. (I even ran with my Linux /home partition as unjournaled HFS+ on one system for a while, although that was a test and I don't recommend you do it on a production system.) AFAIK, the unjournaled HFS+ should be as reliable as the journaled version; a journal serves as a shortcut for repairing a disk after a power failure or system crash, so it's a time-saver, not a reliability improver. FAT is another option, but only if you can live with its 4 GiB file-size limit.

---

