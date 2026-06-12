---
title: "Read-only file system"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by vasanaditya on 2007-11-07
hey 
i am trying to mount my external harddisk . i followed the instructions on some site which told me to create a directory called /dev/sda1 . then mount using the following code :
mount /dev/sda1 /mnt/external

---

### Post by taurus on 2007-11-07
Is it ntfs filesystem?  If it is, then you need to install and use ntfs-3g if you want to write to it.

Which release are you running right now?

---

### Post by NeoLithium on 2007-11-07
Is it an external device that you used with Windows? It could be an NTFS file system, in which case you shouldl check this out, to help mount & use the drive: [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by vasanaditya on 2007-11-07
yes , it is ntfs filesystem 
im running kubuntu 7.0.4

---

### Post by picopir8 on 2007-11-07
EDIT: I was too slow, already posted.

---

