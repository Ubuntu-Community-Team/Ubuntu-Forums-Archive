---
title: "Unable to change owner of folder"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Gerwich on 2007-05-12
My windows partition is set as being owned by root, and I can't seem to change the owner.
This is what happens when I try to change it:
```
kevin@kevin-ubuntu:/$ sudo chown kevin:kevin /windows
chown: changing ownership of `/windows': Operation not permitted

```

---

### Post by taurus on 2007-05-12
Chmod won't work with ntfs or vfat filesystem.

---

### Post by Gerwich on 2007-05-12
How do I change permissions for it, then?

---

### Post by taurus on 2007-05-12
What is the filesystem of that partition, ntfs or vfat?

```
sudo fdisk -l
df -h
```

---

### Post by Gerwich on 2007-05-12
It's FAT32.

---

### Post by taurus on 2007-05-12
What partition is it and where do you mount it?

```
df -h
```

---

### Post by Gerwich on 2007-05-12
It's sda3 and it's mounted right on root (/, not /root). 
That's another oddity, for some reason it's identifying my partitions as sda. I thought that sd referred to SCSI drives, but my hard drive is ATA.

---

### Post by Enverex on 2007-05-12
You want to mount it allowing everyone access. Erm, that's "-o umask=0000" appended to the mount command if I remember correctly.

IDE drivers as of .20 (or maybe .19) now use the SCSI subsystem in the kernel so everything is SD/SR.

---

### Post by Gerwich on 2007-05-12
Actually, I checked in fstab and it already had umask=007, so i just changed that to umask=0000, and that fixed it.  
I didn't need to add -o. (Oops, I forgot to mention that it was auto mounted before, didn't I?) 

Thanks!

---

### Post by Enverex on 2007-05-12
> **Gerwich said:**
> Actually, I checked in fstab and it already had umask=007, so i just changed that to umask=0000, and that fixed it.  
I didn't need to add -o. (Oops, I forgot to mention that it was auto mounted before, didn't I?) 

Thanks!

The -o means option and that's just when you're using the mount command, not in fstab, as you worked out it's just "as-is" in there.

---

