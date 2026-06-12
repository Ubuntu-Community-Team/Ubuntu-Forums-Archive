---
title: "windows HD to ubuntu??"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by steeeler58 on 2006-12-02
I am wondering if I can take a HD from a windows PC and install it in a comp running ubuntu with out losing the data on the HD? I need to have my windows comp fixed and would like to access my extra HD while the motherboard on my windows PC is being fixed. What do you think??

Thanks!

---

### Post by compwiz18 on 2006-12-02
Should work.

---

### Post by taurus on 2006-12-02
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by creaturex on 2006-12-02
Only possible problem is linux can't (safely) write to an ntfs partition. fat32 is fine though. If youre willing to risk data corruption there's a mostly safe program called 3gntfs or something. search the forums for threads about ntfs to learn how.

---

### Post by taurus on 2006-12-03
ntfs-3g.

---

### Post by Chinkostu on 2006-12-03
read access for NTFS (XP's default) is fairly easy, it involves creating an entry in fstab and a directory in /media. write access to NTFS is experimental, so don't try it.

FAT filesystems are fine though

---

