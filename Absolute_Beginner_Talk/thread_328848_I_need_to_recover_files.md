---
title: "I need to recover files"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by Jtrybyne on 2006-12-31
I am totally new to linux.  I made an Ubuntu livecd.  When my laptop tries to boot into windows it says that there is a missing or corrupt system file.  So i booted into Ubunto from the CD.  I want to recover some files from my HD.  How do I mount my HD so I can access the files?  In the help app it says to go to system administration disks.  But there is no disks or disk manager in the menu.  How do I get to my files??  Thanks.

---

### Post by bruenig on 2006-12-31
You need to find out the name of the partition that it is on. To do that do
```
sudo fdisk -l
```

Whatever the Device boot (/dev/whatever) name is, that is what you put into the mount command at the bottom of this post.

Now you need to create a mount point and then mount the disk. Open a terminal, Applications>Accessories>Terminal
```
mkdir windows
sudo mount -t ntfs /dev/whatever ~/windows
```

Now you should theoretically be able to view your stuff in the file manager. Also if your windows is fat32, change ntfs above into vfat.

---

### Post by Jtrybyne on 2006-12-31
Thanks.

---

### Post by citaworvk on 2006-12-31
alt+0

---

