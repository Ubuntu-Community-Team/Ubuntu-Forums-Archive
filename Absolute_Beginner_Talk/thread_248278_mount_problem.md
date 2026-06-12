---
title: "mount problem"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by essendon on 2006-08-31
i there.
I am trying to mount anouther hard drive that already has a full version of ubuntu 5.10 on it. The primary drive is running ubuntu 6. In the partitions tab of the disk manager, the status for the secound drive reads "inaccessible" and it can't enable it.

I have to transfer infomation from one drive to the other. I tried using the second drive as a master, but the xwindows system didn't load.

---

### Post by richbarna on 2006-08-31
What to do if your post isn't answered :)
[http://www.ubuntuforums.org/showthread.php?t=82471](http://www.ubuntuforums.org/showthread.php?t=82471)

---

### Post by bodhi.zazen on 2006-09-01
> **essendon said:**
> i there.
I am trying to mount anouther hard drive that already has a full version of ubuntu 5.10 on it. The primary drive is running ubuntu 6. In the partitions tab of the disk manager, the status for the secound drive reads "inaccessible" and it can't enable it.

I have to transfer infomation from one drive to the other. I tried using the second drive as a master, but the xwindows system didn't load.

Need more information. How is the second HD partitioned?

Assuming Ubuntu 5 is on the first partition of the second drive:

Make a directory (mount point)
Mount.

Ex
```

sudo mkdir /mnt/hdb
sudo mount /dev/hdb1 /mnt/hdb
```

If this scheme is not working, error message??

***Err... Nothing like a dual thread.***

---

