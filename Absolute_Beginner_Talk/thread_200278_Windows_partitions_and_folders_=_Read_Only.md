---
title: "Windows partitions and folders = Read Only"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-06-20
Even if I do gksudo nautilus and move to a windows ntfs folder I can't change permissions,because it says: Read Only Disk ??  Thanks

---

### Post by aysiu on 2006-06-20
NTFS is read-only from Linux... unless your data isn't precious to you.

---

### Post by Drakkor on 2006-06-20
Sorry for being dense here,so I guess I can't write or save things in windows,from linux ?  Just seeing what the capabilites are.. :p

---

### Post by siccness on 2006-06-20
[QUOTE=Drakkor]Sorry for being dense here,so I guess I can't write or save things in windows,from linux ?  Just seeing what the capabilites are.. :p[/QUOTE]

You shouldn't write to NTFS drives from Linux. It is possible but from what I heard it's a great way to lose your data.

---

### Post by aysiu on 2006-06-20
You can, however, write to Linux from Windows, with the help of [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by anaconda on 2006-06-20
And there used to be captive-NTFS for linux.. Where linux searched windows NTFS-drivers from windows partition, and used those thorough emulator. It was reliable, but a bit slow.

Dont know if it is still around..

---

