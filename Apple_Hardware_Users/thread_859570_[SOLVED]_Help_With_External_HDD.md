---
title: "[SOLVED] Help With External HDD"
date: 2008-07-14
forum: Apple Hardware Users
---

### Post by DGortze380 on 2008-07-14
First, I apologize, this is an OS X question, but I always get more mac guys here than the other forums.

I'm running a MacBook1,1 with Tiger. I always shut it down at night, but the other night I left is hibernating and made a dumb mistake, I unplugged my external and the next morning opened the computer and it came out of hibernation with a warning saying a device was removed incorrectly. (obviously the external was still mounted.

So now when I plug the drive in, my HFS+ partition automounts to the desktop (I also have a FAT32 partition that will does not automount anymore), but I can't access it, Finder locks up, need to relaunch. I open disk utility to try and fix the disk disk utility locks up have to force quit. Tried to access the partition via terminal, shows both partitions mounted, but terminal locks up when I CD to either partition. Tried to unmount via terminal (sudo diskutil unmount /Volumes/DriveName) and terminal locks up.  Tried the same thing in the terminal on my recovery disk, same problem. Had to force quit terminal. Checked ownership and permissions, all are correct.

The drive mounts, reads, and writes correctly on Ubuntu, but OS X is having some real issues. I can reformat if needed, but obviously the file system is ok, I'd like to fix whatever is wrong so OS X access it correctly again.

Any thoughts?

---

### Post by cyberdork33 on 2008-07-15
You might try doing a filesystem repair from Linux. From the FAQ:
[http://ubuntuforums.org/showthread.php?p=2346494#post2346494](http://ubuntuforums.org/showthread.php?p=2346494#post2346494)

---

### Post by DGortze380 on 2008-07-22
Upon advice from Mac-Forums, I've assumed that the problem is my FAT32 partition, not HFS+.

I don't know why I didn't think of this sooner but, working off that assumption my solution was as follows:

Boot Ubuntu. 
Back-up FAT32 partition to HFS+ partition.
Use dd command to write zeros to FAT32 Partition. (dd if=/dev/zero of=/dev/sdb2)
Reboot to OS X, FAT32 still won't mount or unmount but I now have access to my HFS+
Backup HFS+ to MacBook HDD
Reformat and never again use a FAT32 partition.

---

