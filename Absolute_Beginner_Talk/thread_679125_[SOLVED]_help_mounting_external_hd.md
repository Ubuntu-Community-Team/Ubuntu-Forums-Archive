---
title: "[SOLVED] help mounting external hd"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by pete_zahuat on 2008-01-26
I am having trouble mounting my external hd.  I have the ntfs config tool but still nothing.  When I plug in the hd, I get this error message:

$LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action...

---

### Post by kindafunnylookin on 2008-01-26
If you boot up with the external HD connected, and powered up, ubuntu should see it. What king of connection is it ?

---

### Post by pete_zahuat on 2008-01-26
usb connection

---

### Post by kindafunnylookin on 2008-01-26
Have you tried rebooting with the drive on? what is the output of
```
sudo fdisk -l
```

---

### Post by pete_zahuat on 2008-01-26
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4771    38323026   83  Linux
/dev/sda2            4772        4864      747022+   5  Extended
/dev/sda5            4772        4864      746991   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

---

### Post by kindafunnylookin on 2008-01-26
Ubuntu is seeing the external disk. [See this thread for mounting it.]("http://http://ubuntuforums.org/showthread.php?t=665842")

---

### Post by pete_zahuat on 2008-01-26
can you please post another link.. that one seems to be dead

---

### Post by kindafunnylookin on 2008-01-26
[This should be OK]("http://ubuntuforums.org/showthread.php?t=665842")

---

