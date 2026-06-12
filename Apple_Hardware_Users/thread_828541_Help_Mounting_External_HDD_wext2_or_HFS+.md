---
title: "Help Mounting External HDD w/ext2 or HFS+"
date: 2008-06-13
forum: Apple Hardware Users
---

### Post by Lycus on 2008-06-13
All right, here's my predicament.

I'm running a MacBook with OS X 10.5.3 and a PC with Ubuntu 8.04 AMD64.

I have a 320GB LaCie drive I want to use between them, but I've encountered problems.

The drive is currently blank, well, as of this post, it's formatted as ext2.

Ubuntu, obviously, can read and write to this. OS X, however, can only read (I've installed Ext2FS, but even when I enable the "Ignore permissions" options in the ExtFSManager, I still cannot write to it).

I've also tried formatting the drive with HFS+, non-journaled, and OS X is fine with that, but Linux doesn't want to mount it. I'm unsure where to go further. Assistance would be appreciated, thanks.

---

### Post by cyberdork33 on 2008-06-13
use fat32.

IDK why your HFS+ partition wouldn't mount, what did you try?

---

### Post by Lycus on 2008-06-13
> **cyberdork33 said:**
> use fat32.

IDK why your HFS+ partition wouldn't mount, what did you try?

I have files larger than 4GB, and the drive is 320GB... I do not want to use FAT32.

I forgot the exact syntax I tried to mount atm, what should I be trying to mount the HFS partition?

---

