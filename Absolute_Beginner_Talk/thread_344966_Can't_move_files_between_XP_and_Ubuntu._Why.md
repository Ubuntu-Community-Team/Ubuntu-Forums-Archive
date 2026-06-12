---
title: "Can't move files between XP and Ubuntu. Why?"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by bodzasfanta on 2007-01-23
Hello!

I can't move my files from Ubuntu to XP partition. Why?
I get a window: access denied. I tried to change the permissions, but it doesn't work.
Any and all help appreciated

---

### Post by meng on 2007-01-23
Ubuntu does not by default have write access to NTFS partitions. If you must have write access, be warned it is relatively new (officially experimental), but search the forums for "howto ntfs-3g"

---

### Post by Happy_Man on 2007-01-23
Since NTFS is not a native Linux format, there will be issues like this unless you log into root. And, changing the permissions on the drive won't work, since I think Ubuntu won't let you. To remedy this, install ntfs-3g (search for it on these forums). It installs drivers for Ubuntu that allow it to read and write to any NTFS partition. Hope this helps!

---

### Post by jvc26 on 2007-01-23
Thats because, in all probability your windows partition is an NTFS partition. NTFS only has read permission my default in Ubuntu. You can get the NTFS read/write beta drivers - don;t have the link to hand I'm afraid but a quick forum search will help, which would allow you to read and write to the disk. The reason being that NTFS is an MS proprietary filesystem and thus Ubuntu does not come with the drivers to read/write it by default.
Il

---

### Post by bodhi.zazen on 2007-01-23
[http://ubuntuforums.org/showthread.php?&t=217009](http://ubuntuforums.org/showthread.php?&t=217009)

---

### Post by bodzasfanta on 2007-01-23
Thank You really much for the helps! Everything goes well.

---

