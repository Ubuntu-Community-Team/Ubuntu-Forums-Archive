---
title: "[SOLVED] ext2 in extended partition is read only"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by fenixphire07 on 2007-11-21
I just installed Ubuntu 7.10. I've placed one ext2 partition as a primary with the filesystem installed there, i have also placed 2 more ext2 partitions in an extended partion along with a fat32 partition. Now for some reason, i cant seem to be able to write to the ext2 partitions in the extended partition, but fat32 partition working fine.

any clues guys?

thanks in advance.

---

### Post by jordanmthomas on 2007-11-21
only do this if you don't already have files on your ext2 partitions whose permissions you care about.
```
sudo chown -R $USER /path/to/ext2/mountpoint
```
, substituting where each partition is mounted, of course (something like /media/disk)
This will give your user ownership (and write permission unless your permissions are odd to begin with)

---

