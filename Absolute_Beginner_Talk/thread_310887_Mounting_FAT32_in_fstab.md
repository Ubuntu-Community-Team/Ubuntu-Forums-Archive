---
title: "Mounting FAT32 in fstab"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by coolboarderguy on 2006-12-02
Hi All,

I have the following in fstab,

/dev/sda4       /mnt/sharefat   vfat    rw.defaults,uid=1000,gid=1000,umask=0000        0       0

but it doesn't load auto. What needs changing? I was following here,
[http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS](http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS))

---

### Post by agustin.g on 2006-12-02
hmmm, the "rw" option is already included in "default", and i think you can delete the "uid", "gid", and "umask" entries... i've added lines on fstab without those entries and it has worked fine...

check [this page](http://www.tuxfiles.org/linuxhelp/fstab.html) for more info

---

### Post by nixternal on 2006-12-02
> /dev/sda4 /mnt/sharefat vfat rw.defaults,uid=1000,gid=1000,umask=0000 0 0

rw.defaults should be rw,defaults

change the period to a comma

---

### Post by coolboarderguy on 2006-12-02
DOH!! Tnx.

---

