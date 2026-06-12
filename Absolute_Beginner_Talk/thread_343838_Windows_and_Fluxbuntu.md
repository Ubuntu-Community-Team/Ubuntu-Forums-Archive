---
title: "Windows and Fluxbuntu"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by helphope on 2007-01-22
Hi everybody.

Finally I got fluxbuntu running on an old laptop.
 I've been searching to see my windows partition and pen drive but to no avail.:confused: 

I've been reading the topics about fluxbuntu without coming across anything which could help me.

Thanks for any hint

---

### Post by jordanmthomas on 2007-01-22
in a terminal, type
```
sudo fdisk -l
```
to find out where your discs are (/dev/sdxy) or something similar.
Then, you can look at Ubuntuguide.org to find out how to mount them (automatically -- /etc/fstab) or manually
[http://www.ubuntuguide.org](http://www.ubuntuguide.org)  <--seems to be down?

(btw, your windows partition will likely be NTFS and your flash drive will be FAT32)

---

### Post by helphope on 2007-01-22
Thanks :)

---

