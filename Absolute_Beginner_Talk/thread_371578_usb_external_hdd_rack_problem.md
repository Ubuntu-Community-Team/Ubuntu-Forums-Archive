---
title: "usb external hdd rack problem"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by stealth_kid on 2007-02-27
i have a machine with ubuntu 6.10 (32bit) and an external hdd rack which can be connected through an usb cable. when i insert the cable into a free usb slot and i power on the rack, the disk is auto-mounted as ntfs (the hdd is formated as ntfs) but i only have read and execute rights, i cannot copy to or delete anything from that partition. i tryed to change the rights and the ownership as root but i cannot, it keeps telling me that the disk is read-only... this is what i get when i type "mount" :
/dev/sdb5 on /media/KARGO type ntfs   (rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8 )
this is what i get when i try "sudo chmod 755 /media/KARGO" :
chmod: changing permissions of `/media/KARGO/': Read-only file system
is there any way i can fix this?

---

### Post by Kateikyoushi on 2007-02-27
NTFS is not writable in default. Read this guide so you can write on it. [LINK]("http://www.ubuntugeek.com/mount-your-widows-partitions-and-make-it-read-and-writable.html")

---

### Post by stealth_kid on 2007-02-27
thank you.

---

