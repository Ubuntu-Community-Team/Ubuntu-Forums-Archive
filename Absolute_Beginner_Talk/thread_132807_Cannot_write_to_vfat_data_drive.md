---
title: "Cannot write to vfat data drive"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by tadashi on 2006-02-19
I setup a vfat data drive so that I can share data between my NTFS and Linux partitions.  Linux setup this drive as /dev/hda5 but root has ownership.  How do I change the /etc/fstab to make this drive readable and writable to anyone?

---

### Post by aysiu on 2006-02-19
```
sudo umount /dev/hda5
sudo cp /etc/fstab /etc/fstab_backup
sudo mkdir /data_drive
sudo nano /etc/fstab
``` Change this line ```
/dev/hda5 /media/hda5 vfat defaults 0 0
``` to this line ```
/dev/hda5 /data_drive vfat iocharset=utf8,umask=000 0 0
``` Save (control-x), confirm (y), and exit (Enter). ```
sudo mount -a
```

---

### Post by tadashi on 2006-02-19
Thanks that did the trick.

---

