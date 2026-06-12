---
title: "mounting"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by Unlockitall on 2007-02-17
im having a little issue mounting a floppy, what is the exact command i should enter in terminal?

---

### Post by bodhi.zazen on 2007-02-17
> **Unlockitall said:**
> im having a little issue mounting a floppy, what is the exact command i should enter in terminal?

```
sudo mkdir /media/floppy
sudo mount /dev/fd0 /media/floppy
```

Permissions depend on the file system on the floppy.  If FAT, try this :

sudo mount /dev/fd0 /media/floppy -o umask=000

If Linux native, use chmod after mounting :)

---

### Post by Unlockitall on 2007-02-17
i did the command specified and recevied, after some clunking noises
> mount: must specify filesystem type

---

### Post by Maestro23 on 2007-02-17
Here's another post discussing floppy mounting.  

[http://www.ubuntuforums.org/showthread.php?t=363870](http://www.ubuntuforums.org/showthread.php?t=363870)

---

