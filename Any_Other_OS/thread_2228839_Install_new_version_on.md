---
title: "Install new version on /"
date: 2014-06-09
forum: Any Other OS
---

### Post by borgward on 2014-06-09
I have an 80GB drive that is partitioned:
/dev/sda1 /         ext4
/dev/sda4/home  ext4
dev/sda2/tmp      ext4

It has Linuxmint 14 on it now. I will be installing Linuxmint17. My understanding is that by having a seperate /dev/home, I can install another linux distro while keeping my /dev/home and hopefully /dev/tmp.

I am not sure how to do this.

---

### Post by bapoumba on 2014-06-10
*Thread moved to **Other OS/Distro Support**.*

---

### Post by buzzingrobot on 2014-06-10
Select manual partitioning (aka 'Something Else'). You will see the existing partitions listed. Select and correctly set up each.  You will want to check the format option for '/', but not for the partitions whose content you want to preserve. The filesystem selected should be the same as it is now, almost certainly ext4.

A backup is always wise, just in case.

---

### Post by borgward on 2015-05-10
Thread is not there

---

### Post by bapoumba on 2015-05-10
> **borgward said:**
> Thread is not there
?
The Other OS section has been revamped and extended quite some time ago.

---

