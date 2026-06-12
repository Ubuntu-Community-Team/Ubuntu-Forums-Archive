---
title: "how do i check a hard disk?"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by Mick8882003 on 2008-04-09
??

---

### Post by tamoneya on 2008-04-09
what is it that you want to check.  If you want to check how fast a harddisk is working you could use hdparm.  If you wanted to see what partition are on a harddisk you should use either fdisk or gparted.

---

### Post by Mick8882003 on 2008-04-09
sorry wanted to check the hd integrity, but its a windows partition.

---

### Post by tamoneya on 2008-04-09
to do that i would run two things```
hdparm -t /dev/sda
```This would test physical disk integrity.

Then I would run windows chkdisk in order to verify the NTFS file integrity.

---

