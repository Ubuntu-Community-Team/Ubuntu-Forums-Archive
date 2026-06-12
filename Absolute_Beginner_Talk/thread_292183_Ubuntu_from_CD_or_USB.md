---
title: "Ubuntu from CD or USB"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-11-03
Is there a way to run ubuntu from CD or USB and save the work (txt files) on USB?:confused: :confused: 

Thansks for any help

---

### Post by rhb on 2006-11-03
If you have a ubuntu Live CD, you can boot it and use a USB drive for storage.  You can go to the disk manager, where you may need to enable access.  It considers the USB drive to be a "hard disk", which seems a little odd.  Click on the right one, then the "partitions" tab, where you can enable access if needed.

What you can't do as easily is to use the USB drive as your root directory.  I expect some ubuntu guru could figure out how to save some of your configuration files to the USB, though.  Presumably if you did that, whenever you booted you would have to browse to the USB drive and run a shell script which would setup the right mount points and symbolic links.

---

### Post by helphope on 2006-11-03
Thanks for answering.

> **rhb said:**
> If you have a ubuntu Live CD, you can boot it and use a USB drive for storage.  You can go to the disk manager, where you may need to enable access.  It considers the USB drive to be a "hard disk", which seems a little odd.  Click on the right one, then the "partitions" tab, where you can enable access if needed.


You mean that the same UBS can be used - once it has been partitioned - both under windows and under linux?:confused:

---

### Post by Klaidas on 2006-11-03
Yes. 
My USB stick worked on linux and on windows by default (its filesystem is FAT, if I remember correctly. )

---

### Post by helphope on 2006-11-03
Thanks

---

