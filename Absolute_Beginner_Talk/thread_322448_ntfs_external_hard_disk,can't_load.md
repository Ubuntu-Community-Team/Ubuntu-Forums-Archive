---
title: "ntfs external hard disk,can't load"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by tim01 on 2006-12-20
hi all
i followed this  [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)  but i cant see or load my hard disk.i was trying to set permission for write.
when i run "sudo pmount-hal /dev/sda1"    i get  "Please boot into Windows TWICE, or use the 'force' mount option." which i did but no change.
i would be greatefull for any help.thanks

---

### Post by kidders on 2006-12-21
Hi there,

I imagine your NTFS partition has something wrong with it ... for instance, it might be flagged as dirty, which pmount would expect Windows to fix for you. If your checks confirm the filesystem is okay, try forcing it to mount, as suggested. Since you'll presumably only be mounting it read-only, the worst that could happen is that Linux might misread bits of the filesystem.

---

