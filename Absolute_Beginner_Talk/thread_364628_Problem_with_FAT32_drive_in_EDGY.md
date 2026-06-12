---
title: "Problem with FAT32 drive in EDGY"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by hansning on 2007-02-18
Hey, linux newbie here, have a problem with getting ubuntu to find the fat32 drive i just made for sharing files between windows and ubuntu.  I don't know how to find the drive in Ubuntu.

I also tried to made that drive Ext2 because i read that XP will work with it, but couldn't find the drive on XP.

I'm doing all of this to use the same ff & tb profiles on XP and Edgy through this HowTo: [http://ubuntuforums.org/showthread.php?t=203524](http://ubuntuforums.org/showthread.php?t=203524)

help?  is ntfs unreliable in ubuntu?

---

### Post by taurus on 2007-02-18
You are trying to do too many things here!  If you want to mount it as fat32, then paste the output of this command from a terminal here.

```
sudo fdisk -l
```

And if you want to convert it to ext3, then you need to install fs-driver in XP so XP can read and write to it, [http://www.fs-driver.org](http://www.fs-driver.org).

And if you want to convert it to ntfs, then you need to install ntfs-3g in Ubuntu so Ubuntu can write to it.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by hansning on 2007-02-18
[IMG]http://www.flickr.com/photos/45225072@N00/394392705/[/IMG]

i'm really newb, so be gentle on the terminal area, as i'm uncomfortable venturing there...

---

