---
title: "How to shrink Mac OS X partition on dual booting MBP?"
date: 2010-05-28
forum: Apple Hardware Users
---

### Post by Halsnalle on 2010-05-28
After four attempts and diverse partition map problems, I finally managed to install successfully clean versions of both Mac OS X Snow Leopard and Ubuntu Lucid Lynx on my old MacBook Pro C2D (2,1) and a new 320 GB HDD, by following these instructions:
[http://bit.ly/beiiHp](http://bit.ly/beiiHp)

Now, I've got a big partition for Mac OS X (286 GB) and a small partition for Ubuntu (30 GB, as well as two smaller partitions for grub and swap). However, I'd like to shrink the Mac OS X partition to, say, 35 GB, and use the freed up 251 GB as a shared partition to keep files for access from both OSs. But Mac OS X Disk Utility won't let me resize the Mac OS X partition (and warns that it might not be a smart thing to do, as the disk has been partitioned for Boot Camp, etc).

Is there some way I can resize the partition, or do I have to start all over again…?

---

### Post by paulo_ on 2010-05-28
I have a MacBook alu 5,1 and had the same problem. And once again, Ubuntu came to the rescue. Just boot from Ubuntu CD and run GParted. This program allows you to shrink hfs+ partitions :)

---

### Post by Halsnalle on 2010-05-29
> **paulo_ said:**
> I have a MacBook alu 5,1 and had the same problem. And once again, Ubuntu came to the rescue. Just boot from Ubuntu CD and run GParted. This program allows you to shrink hfs+ partitions :)

Thanks, that seems an easy solution. And it won't mess up the partitions?

---

### Post by paulo_ on 2010-05-30
> **Halsnalle said:**
> Thanks, that seems an easy solution. And it won't mess up the partitions?

Well, it didn't mess up here. Everything is ok.

---

### Post by Halsnalle on 2011-02-08
> **paulo_ said:**
> Well, it didn't mess up here. Everything is ok.

Worked for me too. Thanks!

---

