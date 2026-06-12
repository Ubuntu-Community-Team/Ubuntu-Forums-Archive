---
title: "Ext HD ntfs"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by koprioni on 2007-11-13
HI there
is there any way to copy some files from ubuntu to my external hard disk(ntfs)?
thnx.

---

### Post by ubnewbie2 on 2007-11-13
In gutsy (7.10) the ntfs driver is included, so I would have thought you could just plug into the usb port and it would be ready to go.

---

### Post by koprioni on 2007-11-13
i have feisty
i tried to copy a file but the "copy" in menu is disabled

---

### Post by Paul820 on 2007-11-13
You can configure your ntfs drives with ntfs-config
> sudo apt-get install ntfs-config

---

### Post by ubnewbie2 on 2007-11-13
I see, I just tried that tool, and it appears that writing to external devices is turned off by default.  So, he just needs to turn that on?  I wonder why it isn't on by default?

---

### Post by koprioni on 2007-11-13
[QUOTE=Paul820;3765390]You can configure your ntfs drives with ntfs-config[/QUOT]

i enabled the "write" to internal and external and i still can't copy with right click->copy and then right->paste
it says i have to be root
how can i login as root?
thnx

---

### Post by Paul820 on 2007-11-13
Do you have the program installed called **ntfs-3g**? I see you are using feisty so it's not installed by default. Install that and it will give you read and write permissions.

---

### Post by koprioni on 2007-11-13
yes i have it(as i see)
ntfs-3g set to manual installed.
no what?

---

### Post by taurus on 2007-11-13
Why don't you unmount it first and then mount it again.

```
sudo umount /dev/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
ls -la /media
```
_Assuming_ /dev/sdb1 is your external USB drive.

---

### Post by ubnewbie2 on 2007-11-13
> **koprioni said:**
> yes i have it(as i see)
ntfs-3g set to manual installed.
no what?

Try opening the file manager as root

```
 gksudo nautilus
```

---

### Post by koprioni on 2007-11-13
~$ sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
fusermount: failed to access mountpoint /media/sdb1: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sdb1 (Pali_Ap'thn_Arxh)
 i get this when i try to remount it

nothing happened with gksudo nautilus
but now, i tried to write and remove from one windows partition i have mounted before and i can
but only in this
Neither at the external drive nor at the other partition

---

### Post by taurus on 2007-11-13
Why don't you just create that mount point and mount it again.

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
```

---

### Post by koprioni on 2007-11-13
worked
thnx very much

---

