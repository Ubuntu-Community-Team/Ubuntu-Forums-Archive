---
title: "New fat32 Partition on ext3"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by jeffreyvergara.NET on 2005-11-17
hello, I have a ext3 HD in slave and I used it for saving my files (video,softwares), I want to create a new fat32 partition, if I use gParted, will it erase the whole ext3 HD if a create a new partition?

---

### Post by Kapre on 2005-11-17
[QUOTE=jeffreyvergara.NET]hello, I have a ext3 HD in slave and I used it for saving my files (video,softwares), I want to create a new fat32 partition, if I use gParted, will it erase the whole ext3 HD if a create a new partition?[/QUOTE]

jeff - I have not tried this but since the file system of linux is different and the files are not scattered (M$), back up all your files on ext3 partition and after that use gParted to resize it.

K

---

### Post by jeffreyvergara.NET on 2005-11-17
what if I just partition my HD both in ext3 and let Window$ installation convert it to fat32? is it possible?

damn this school project! now I need to install Window$ again on my Linux box..

---

### Post by zerhacke on 2005-11-17
Just a note, if you're going to create the fat32 partition in order to share files between a Ubuntu and Windows dual boot setup, have Windows create the partition instead of Linux.  Sometimes Windows can't see fat32 partitions created by Linux.

---

### Post by jeffreyvergara.NET on 2005-11-17
will I be able to make a partition without formatting the drive?

---

