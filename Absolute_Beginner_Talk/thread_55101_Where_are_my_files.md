---
title: "Where are my files?"
date: 2005-08-07
forum: Absolute Beginner Talk
---

### Post by sleeper on 2005-08-07
When I run UBUNTU from Live CD, where does it put the files I save? (I presume they are somewhere in my hard disk, but I just can't find them -  either from Linux or Windows boot.)

---

### Post by cwaldbieser on 2005-08-07
Unless you mount a filesystem from your hard disk, everything is probably just saved in a RAM filesystem.  That means when the power goes off, *poof*, the files are gone.  

If you have a USB flashdrive or something of that nature, it is probably most convenient to just copy your files there before powering down.  

If your hard drive has a partition you can write to (ext2, ext3, ReiserFS, fat32, etc. -- *not* NTFS) then you could mount that and write directly to the hard drive.

---

