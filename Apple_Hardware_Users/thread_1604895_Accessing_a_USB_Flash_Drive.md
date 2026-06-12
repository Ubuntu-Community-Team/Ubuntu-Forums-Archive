---
title: "Accessing a USB Flash Drive"
date: 2010-10-24
forum: Apple Hardware Users
---

### Post by georgepag on 2010-10-24
I have a simple command question that I haven't found the answer to yet.  I have a usb flash drive plugged in to my newly created Ubuntu system.  A df command shows this:

george@george-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdi1            231594420   8825300 211004724   5% /
none                   1025976       436   1025540   1% /dev
none                   1030196       664   1029532   1% /dev/shm
none                   1030196       212   1029984   1% /var/run
none                   1030196         0   1030196   0% /var/lock
none                   1030196         0   1030196   0% /lib/init/rw
/dev/sdj1              7808768     17152   7791616   1% /media/8G FLASH
george@george-laptop:~$ 

How do I change my directory to the flash drive?  cd doesn't work.

Thanks

---

### Post by sikander3786 on 2010-10-24
```
cd /media/8G\ FLASH
```

Case sensitive and \ followed by space where the file name contains a space.

If it results in an error, post it.

---

