---
title: "partimage"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by jd65pl on 2006-08-03
Hi,

This is what i have done

1. Copied my ubuntu install using partimage
2. Restructured my partitions on hd0
3. Restored my ubuntu install to my new partition

The only problem I am experiencing is that it appears that my partition has 21gb used?!? when infact my ubuntu was only previously 3gb!?

This is shown when i view the drive in gparted and the resource manager.

Does anyone have any ideas?

Thanks

J

---

### Post by OU812 on 2006-08-04
If found this

> Restoring an image into a partition is an easy operation. You must specify the image file to use (it will only be read), and the partition to restore (it will be overwritten). The only extra option you can choose is Erase free blocks with zero values. If this option is enabled, all blocks which are not used are erased with zero bytes. This may be useful if you want to be sure that the data which were on the partition before this operation are fully erased. If this option is disabled, old data which was on currently unused blocks can be accessed (with some difficulty), because nothing is written on these blocks. These old data can be read with tools such as dd (GNU convert and copy). 

at [http://www.partimage.org/Partimage-manual](http://www.partimage.org/Partimage-manual)

Hope it helps.

john

---

### Post by viper on 2006-08-04
GR8 link i was looking for this an hour ago thx:p

---

