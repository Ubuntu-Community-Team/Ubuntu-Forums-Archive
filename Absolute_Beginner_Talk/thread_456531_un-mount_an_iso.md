---
title: "un-mount an iso?"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Pizzarth on 2007-05-27
I tried ejecting my ipod. to my surprise, I couldn't. with no programs running.

then I remembered, I mounted an iso from the ipod into mount by through this method:

```
mount -o loop -t iso9660 filename.iso /mnt/iso
```

I was hoping someone would tell me how I could safely unmount it and be able to eject my ipod?

Thank you

---

### Post by Ek0nomik on 2007-05-27
```
sudo umount /dev/xxx
```

Where xxxy is your identifier.  If you don't know what it is, type:

```
sudo fdisk -l
```

Look for something like sdb1, sdbc1, etc.

Cheers!

---

### Post by juxtaposed on 2007-05-27
Using the unmount command never seemed to work for me (seemed to give me a "this thing isn't mounted" or something error), but this worked:

sudo umount -f /media/isomount

replace /media/isomount with wherever you mounted it.

---

### Post by Pizzarth on 2007-05-27
great, it worked :) Thanks both of you.

---

