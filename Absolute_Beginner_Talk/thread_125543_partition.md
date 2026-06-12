---
title: "partition"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by Icebear on 2006-02-04
I want to use gpart to resize my ext3 drive a bit smaller and then to make a small fat32 partition. I do not have the net so I loaded gpart from the ubuntu home site and then dpk to my computer. But when I run gpart it shows all the partitions but they are have a picture of a lock next to them, so is there a instruction I am missing which lets me to open the drives up or  am I still need to download a subpart for gpart.

---

### Post by mirons on 2006-02-04
I don't know gpart as I use gparted (which is supported by the ubuntu community). I just try to guess what it could be the cause of the lock:
1) You are not running gpart as superuser
2) Most likely you don't have unmounted the partitions you want to work on.
If you are running the program as root, and the partition is not mounted  I can't see any other reason why it shouldn't work.

---

### Post by Icebear on 2006-02-04
sorry the programe is gparted I did not remembered the full name.

---

### Post by xmastree on 2006-02-04
gparted won't run unless you're root. The lock means it's mounted and therefore you can't resize it. Right click on the lock and select unmount, then you can resize it.

---

