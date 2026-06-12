---
title: "How to rip a DVD/CD into an image?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2008-01-21
Does anyone know how to rip a game CD into an .ISO or .IMG format? Or..any other type of image format, as long as it works :P, a GUI method is..preferred, but, if there is none, can someone point me to a how to? Thanks a lot

---

### Post by Lostincyberspace on 2008-01-21
when you insert a disk it will show an icon on the desktop right click on it and select copy disk. Once there set it to copy disk to: file. and it will create an iso for you.

---

### Post by jeffus_il on 2008-01-21
In a terminal: ```
dd if=/dev/cdrom of=my_cd_image.iso
```

---

### Post by lmart on 2008-01-21
using xubuntu 7.10

the following command does not work
dd if=/dev/cdrom of=my_cd_image.iso

get the error message
dd:  '/dev/cdrom/': not a directory


get the same error message if type the command
dd if=/dev/cdrom/ of=my_cd_image.iso

---

### Post by jonabyte on 2008-01-21
> **lmart said:**
> using xubuntu 7.10

the following command does not work
dd if=/dev/cdrom of=my_cd_image.iso

get the error message
dd:  '/dev/cdrom/': not a directory


get the same error message if type the command
dd if=/dev/cdrom/ of=my_cd_image.iso

try sudo...?

---

### Post by Thund3rstruck on 2008-01-21
> **lmart said:**
> using xubuntu 7.10

the following command does not work
dd if=/dev/cdrom of=my_cd_image.iso

get the error message
dd:  '/dev/cdrom/': not a directory


Yea, you need to validate that path. On my laptop the device actually appears as /dev/cdrom0. When it's mounted it appears as /media/cdrom0.

---

