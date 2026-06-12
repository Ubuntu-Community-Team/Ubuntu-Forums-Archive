---
title: "How to share pendrive over the LAN?"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by xdefconx on 2008-01-30
Hye all!!

Can someone guide me how i can share my pendrive on my Ubuntu over the LAN? Let say if can be sharing it is once i unplug that pendrive, it is i have to do some configuration again? It is can be done to configure at once that after that no need to reconfigure it after i unplug that pendrive than plug again into my Ubuntu?

Thanxs for advice.

---

### Post by dcstar on 2008-01-30
> **xdefconx said:**
> Hye all!!

Can someone guide me how i can share my pendrive on my Ubuntu over the LAN? Let say if can be sharing it is once i unplug that pendrive, it is i have to do some configuration again? It is can be done to configure at once that after that no need to reconfigure it after i unplug that pendrive than plug again into my Ubuntu?

Thanxs for advice.

If you label the partitions on your USB drive then it will always be mounted using those names, so you should be able to consistently share any folders on the drive.

---

### Post by xdefconx on 2008-01-30
> **dcstar said:**
> If you label the partitions on your USB drive then it will always be mounted using those names, so you should be able to consistently share any folders on the drive.

Hye **dcstar**! Thanxs for ur reply which i really happy to know that can be done. However, if u dont mind can u explain/guide me technically how to configure it. Did u mean by "label the partitions" is give a name on my pendrive? And also may i know what  mean by "mount" ? can u teach me how to mount?

~*newbies user on Ubuntu*~

Huhuhuhuh

---

### Post by dcstar on 2008-01-30
> **xdefconx said:**
> Hye **dcstar**! Thanxs for ur reply which i really happy to know that can be done. However, if u dont mind can u explain/guide me technically how to configure it. Did u mean by "label the partitions" is give a name on my pendrive? And also may i know what  mean by "mount" ? can u teach me how to mount?

~*newbies user on Ubuntu*~

Huhuhuhuh

Do a search on labelling filesystems - there is (usually) a different command for each type (DOS/NTFS/EXT3 etc. etc.)

You won't need to know about "mount", that is what will happen automatically when you plug in the drive (and you can get detailed explanations by doing a search on that term).

You can share the drive by going into the /media directory and right-clicking the drive name (if you have Samba installed and working).

I have just tested sharing my USB drive, and the only issue was allowing Samba permissions to access it - which I did by giving "Others" create and delete access to the share.

---

### Post by xdefconx on 2008-01-30
> **dcstar said:**
> Do a search on labelling filesystems - there is (usually) a different command for each type (DOS/NTFS/EXT3 etc. etc.)

You won't need to know about "mount", that is what will happen automatically when you plug in the drive (and you can get detailed explanations by doing a search on that term).

You can share the drive by going into the /media directory and right-clicking the drive name (if you have Samba installed and working).

I have just tested sharing my USB drive, and the only issue was allowing Samba permissions to access it - which I did by giving "Others" create and delete access to the share.

Thanxs for ur info! Really appreciate it.

---

