---
title: "USB Drive wont automount now"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by ducamie on 2006-12-17
Im running xubuntu edgy and my external hard drive has been working all week, when i'd turn it on , a little icon would appear on my desktop, but today when i plug it in, nothing.

Any ideas?:neutral:

---

### Post by benuski on 2006-12-17
Did you happen to unplug it from your computer without unmounting it first?  I did that once, and wrecked my boot sector on the drive...

Even if you didnt. run this:

```
sudo fsck.vfat -a /dev/sda1 
```

And replace sda1 with whatever your drive is, as long as its formatted in FAT32.

---

### Post by ducamie on 2006-12-17
its ntfs ](*,)

---

### Post by benuski on 2006-12-17
Try installing "ntfsprogs" if you haven't already, and then attempt to use the ntfsfix command on that drive... thats about all I can think of, save booting into windows and trying to fix it from there.

---

### Post by ducamie on 2006-12-17
thanks

i'll have a go with that

---

