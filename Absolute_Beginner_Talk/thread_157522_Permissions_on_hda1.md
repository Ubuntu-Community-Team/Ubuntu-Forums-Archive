---
title: "Permissions on hda1"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2006-04-09
I have my drive partitioned into hda1 (running Windows), and then one for my Linux OS.  I am installing Dapper, so I want to backup my files, but I cannot transfer them from Linux to hda1.  When I use nautilus in the superuser mode and try to add files to hda1, it tells me that it is read-only.  Is there any way I can change this?

Thanks.

---

### Post by aysiu on 2006-04-09
NTFS *is* read-only from Linux.

---

### Post by ubernoob on 2006-04-09
ntfs is set as read only as default as the writing is not stable. See wiki for more information: [https://wiki.ubuntu.com/NTFSReadWrite](https://wiki.ubuntu.com/NTFSReadWrite)

---

