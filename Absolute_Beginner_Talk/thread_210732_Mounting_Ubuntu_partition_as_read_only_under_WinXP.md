---
title: "Mounting Ubuntu partition as read only under WinXP"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by WaterWalker on 2006-07-07
Is it possible to mount your Ubuntu-partition as a read-only when your in Windows?
I've tried fs-driver, but apparently it's only possible to mount it with full read/write privileges.

---

### Post by ovimunt on 2006-07-07
If your Ubuntu uses ***ext3*** or ***ext2*** file system there's no way to access the partition in Windows. 

Ubuntu can be installed on a FAT32 partition which Windows will access for read/write by default.

---

### Post by Kobalt on 2006-07-07
> **ovimunt said:**
> 
Ubuntu can be installed on a FAT32 partition which Windows will access for read/write by default.

Can it be installed on FAT32 partitions ? I thought that wasn't possible...

---

### Post by ovimunt on 2006-07-07
Well... I don't actually know for sure. I've never tried it myself. I just know it does give you the option to format the partition as FAT32 when you install.

---

### Post by thunderfox933 on 2006-07-07
you can read it under windows use this program

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Use at own risk

---

### Post by mvaniersel on 2006-07-07
> 
If your Ubuntu uses ext3 or ext2 file system there's no way to access the partition in Windows.

That's definitely not true. I'm using a driver called [ext2ifs]("http://www.fs-driver.org/") that enables me to access ubuntu partitions just fine. On my work PC, / is on O: and /home is on N:

It is all read-write though. It's apparently not possible to make the drives read-only.

You could install ubuntu on FAT32, but then you lose all permission information, so I would recommend against that.

---

### Post by crxyem on 2006-07-07
> **ovimunt said:**
> If your Ubuntu uses ***ext3*** or ***ext2*** file system there's no way to access the partition in Windows. 

Ubuntu can be installed on a FAT32 partition which Windows will access for read/write by default.

Not true my friend. take a look at these plugins for windows. 

explore2fs [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)
explore2fs I believe is read only 

EXT2IFS [http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)
EXT2IFS is a read only driver

---

### Post by WaterWalker on 2006-07-07
explore2fs solved my problem, thanks everybody

---

