---
title: "buggy hfsmode unmount"
date: 2010-05-26
forum: Apple Hardware Users
---

### Post by gghose on 2010-05-26
I'm using the Ubuntu Netbook Remix on a network with 3 partitions:NTFS, ext4, and hfsplus.

Once I turned off journaling, I was able to mount the hfsplus partition read/write, which is very nice since I can use it as a common home directory between OS X and Ubuntu.

BUT,

without fail, the partition is not unmounted cleanly. When I reboot into OS X, it has to do a long fsck on the parition, and when I reboot into Ubuntu, it just gives up and mounts the partition read-only.

Has anyone else encountered this problem? Any solutions?

---

