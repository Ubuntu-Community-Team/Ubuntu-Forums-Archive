---
title: "SD card stuck read-only"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Skidlz on 2007-04-28
I have a SD card I am using in my GP2X (portable game system *running linux* ^_^) that is always detected as read only. When a normal user is says I do not have permission to write/deleteI but, when I use sudo nautilus, I get a read only message. have made sure that the lock on the side of the card is off. I have used chmod. And I have tested the card under windows. It works perfectly under windows but is stuck as read only in ubuntu 7.04. It does have some corrupt files on it from when it wouldn't let me eject it and I had to just pull it. I can back up all the data so formatting is an option. Any help would be greatly appreciated.

Thank you!

---

### Post by Najand on 2007-04-28
Is it NTFS?

---

### Post by Skidlz on 2007-04-28
FAT16 it would seem.

```
Disk /dev/sda: 502 MB, 502267904 bytes
4 heads, 19 sectors/track, 12907 cylinders
Units = cylinders of 76 * 512 = 38912 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               4       12908      490376+   6  FAT16
```

---

