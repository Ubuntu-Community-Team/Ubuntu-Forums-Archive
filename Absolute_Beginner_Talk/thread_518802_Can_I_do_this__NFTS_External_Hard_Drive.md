---
title: "Can I do this?  NFTS External Hard Drive?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by arielette on 2007-08-06
Hello:

Is there any way I can get unbuntu to let me save files to my FreeAgent ntfs external hard drive?  It was formated at one time with ext3 and I could not change the file permissions to write to it.  I even tried logging on as root and I could not manage it.  Why can't I control this?????

Thanks.....:confused:

---

### Post by bukwirm on 2007-08-06
[http://www.linux-ntfs.org/]("http://www.linux-ntfs.org/")

---

### Post by por100pre1 on 2007-08-06
Another way is to change it to FAT32, but it is not a good idea if you need to save large files, lets say, 4GB or bigger...

---

### Post by Inxsible on 2007-08-06
you can use NTFS drives natively in Linux for read access. For write access, you will need to install ntfs-3g.

For EXT3 drives, you can easily change permissions and ownership. But lets not go into that, since you already changed your file system to NTFS :)

---

### Post by arielette on 2007-08-06
Thanks for all the info!  I installed ntfs-3g and it worked a charm.  :KS

---

