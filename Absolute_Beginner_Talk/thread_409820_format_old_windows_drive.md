---
title: "format old windows drive"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by adza on 2007-04-15
hi there, i've just installed a second sata for my windows partition (i know i know, i'm working on it!!) and that has freed up another 160GB IDE drive that i want to make into my second linux drive... my question is, how do i format this drive into ext3 and erase all content so i have a second, fresh drive for linux?

---

### Post by BoneKracker on 2007-04-15
```
man fdisk

fdisk /dev/<whatever>

man mkfs

mkfs.ext3 /dev/<whatever><part#>
```

It sounds like "whatever" is probably hdb.

Fdisk will create a dos disklabel for you and ask you what partitions you want to create.  it's pretty easy.  read the man page.  c to create; d to delete; etc.

mkfs is like "format"

---

