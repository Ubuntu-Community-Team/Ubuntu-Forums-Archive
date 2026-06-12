---
title: "How to move Directory"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by Jubal on 2006-02-01
I made a total beginner mistake.  I mounted my large second hard drive as /storage.  I now know I should have mounted it at /home/username/storage.  Is it possible to move this directory?

---

### Post by aysiu on 2006-02-01
It's actually a lot easier than *moving* the directory.
Just unmount it, change the mount point, and remount it.

Is it mounted through /etc/fstab or did you manually mount it?

---

### Post by Jubal on 2006-02-01
It was mounted at install.  I see how to change the mount point in /etc/fstab.  How do I unmount the drive?

---

### Post by aysiu on 2006-02-01
Go to Applications > Accessories > Terminal and type these commands:

```
sudo umount /storage
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```

Change the line that has /storage in it to say /home/jubal/storage, then save (Control-X), confirm (y), and exit (Enter). Then ```
sudo mount -a
```

---

### Post by Jubal on 2006-02-01
Thank you I was actually trying to do 

sudo unmount /storage

I am getting there!

---

### Post by aysiu on 2006-02-01
Sometimes abbreviations make things more confusing than the full word. I can't tell you how many times I've typed ```
/user/bin
``` instead of ```
/usr/bin
```

---

