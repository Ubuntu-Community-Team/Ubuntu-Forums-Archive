---
title: "Change File Premission For Windows Drive"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by battleroyalex on 2006-07-03
My windows mounted drive will let me read but not write to it, How do I change the premissions of it to get total control over it? Right clicking and going to premissions is all grayed out :(

My mounted windows drive is located as /media/sda1

---

### Post by professor_chaos on 2006-07-03
linux at the moment, cannot safely write to a ntfs filesystem that is ohh so common format in win XP. What is your filesystem of the windows partiton?

---

### Post by battleroyalex on 2006-07-03
ntfs, so theres no way possiable?

---

### Post by aysiu on 2006-07-03
There are ways *possible*, but they're experimental, so you may lose a lot of data. In other words, NTFS is read-only from Linux.

You're much better going the other way around and modifying Ubuntu files from Windows using this driver: [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by MaximB on 2006-07-03
and if I have winxp with fat32 partition (witch I have not...but let say I have) will touse "gray" bottens become selectable ?

---

### Post by hardfire_avk on 2006-07-03
What bout FAT 32. How can i write on those.

---

### Post by Apple 101 on 2006-07-03
Yes.  It is perfectly safe to read/write on Fat32 partitions.

---

### Post by aysiu on 2006-07-03
[QUOTE=hardfire_avk]What bout FAT 32. How can i write on those.[/QUOTE]
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Jagot on 2006-07-03
Or:

[https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html](https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html)

---

