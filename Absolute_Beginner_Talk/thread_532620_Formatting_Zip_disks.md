---
title: "Formatting Zip disks"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by macruadhi on 2007-08-22
I just got a used Zipdrive, I've searched, but I can't find out how to format the disks for linux. Please help.


Thank you,
Eric

---

### Post by ddrichardson on 2007-08-24
```
/sbin/mkfs &#8211;t vfat /dev/zip
``` Should do the trick. There's more info [here]("http://www.eos.ncsu.edu/labs/zip.html").

---

### Post by macruadhi on 2007-08-24
Tried it and all I got was eric@eric-laptop:~$ /sbin/mkfs –t vfat /dev/zip
mke2fs 1.38 (30-Jun-2005)
mkfs.ext2: invalid blocks count - vfat

---

### Post by Paulmd on 2007-08-25
> **macruadhi said:**
> Tried it and all I got was eric@eric-laptop:~$ /sbin/mkfs –t vfat /dev/zip
mke2fs 1.38 (30-Jun-2005)
mkfs.ext2: invalid blocks count - vfat

Are you certain that your drive and media are OK? 

Also, about the zip drive, they come in many flavors:

Internal IDE
Internal SCSI (these are often Apple ROM'd)

External Parallel Port
External SCSI
External USB

I've not yet seen a firewire model, but wouldn't be all that surprised if there was one.

As well as various drives for laptops.  What kind to you have?

---

### Post by schorsch on 2007-08-25
You need to install "dosfstools" if you want to create a vfat partition. Then you will be able to
```
sudo mkfs.vfat /dev/zip
```
Or do you want to create another filesystem type?

---

### Post by macruadhi on 2007-08-25
I already had dosfstools install, I would like it to be writeable on Linux and readable on windows. And thanks to all for the help you've given so far.

---

### Post by ddrichardson on 2007-08-25
vfat is the best option then, size limitations aren't an issue given zips relatively low size.

---

### Post by schorsch on 2007-08-25
> **macruadhi said:**
> I already had dosfstools install, I would like it to be writeable on Linux and readable on windows. And thanks to all for the help you've given so far.
Have you already tried the command I mentioned in my last post? If so and it did not work what is the error message? And I second that vfat will be the filesystem that will cause the least trouble ....

---

