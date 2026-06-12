---
title: "Change permissions to read only hard drive"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by Yak on 2006-11-08
Hi

I have a 2 hard drives. HD1 has Windows Xp installed on one partition, Ubuntu on another partition and a third partition for miscellaneous files. (Note: I am not counting the swap partition for Linux). HD2 is a general drive for my music, movies etc.

The problem: both the third partition of HD1 and the whole of HD2 are read only. Is there any way I can change the permissions of these, or do I need to unmount them and remount them with full permissions? If so, how do I mount/unmount? (Note: I did not mount them in the first place, it was all done automatically during the installation).

Any help is greatly appreciated.

---

### Post by kerry_s on 2006-11-08
Are they ntfs? If so you have to add support or you'll screw them up. Linux still has poor ntfs support and it's all ways a risk writing to them.

---

### Post by Yak on 2006-11-08
Yes, both HD's are NTFS. How do I add support and is it not already there with the latest version of Ubuntu?

The partition where Ubuntu is installed is also NTFS but I haven't had any problems with it.

---

### Post by Yak on 2006-11-08
Never mind, I found a How-To using ntfs-3g.

---

### Post by dannyboy79 on 2006-11-08
> **Yak said:**
> The partition where Ubuntu is installed is also NTFS but I haven't had any problems with it.

Almost IMPOSSIBLE I believe. The install wouldn't have let you install to it since it can't write to it by default. Check again, do a sudo fdisk -l and you'll find out what it is.

---

