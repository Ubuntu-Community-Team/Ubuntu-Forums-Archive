---
title: "Mounted ext3 partition, hide from other users"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by C-A on 2007-02-25
I have mounted an ext3 partition:

> /dev/hdc1 /drive-media ext3 defaults 0 0

I set permissions as:

> sudo chown -R uname:uname /media/drive-media
sudo chmod -R 755 /media/drive-media

However, I would like these partitions to be visible for my user only.

This partition was originally formatted as fat32 and mounted with a group id:

> /dev/hdc5 /media/windows/ -t vfat -o iocharset=utf8,gid=1001,umask=000 

Will including the group id in the fstab entry work for the ext3 partition also?

---

### Post by C-A on 2007-02-25
> **C-A said:**
> Will including the group id in the fstab entry work for the ext3 partition also?

Or is there better way to mount the partition for my user only where others users can not see it or have access to it?

---

### Post by C-A on 2007-02-25
> **C-A said:**
> Or is there better way to mount the partition for my user only where others users can not see it or have access to it?

I tried adding the group id entry to my fstab but that did not seem to be the trick.
The mounted partition is currently set to me as the user and me as the user group so how come other users can still see the partition and access its contents?

---

### Post by yabbadabbadont on 2007-02-25
You can't keep them from seeing that it exists, but you can prevent them from viewing the contents.

sudo chmod -R go-rwx /media/drive-media

---

### Post by randiroo76073 on 2007-02-25
What I did was put "mnt" in my /home/username folder for my access only, the only thing I have in /media is cd, dvd & usb hdd.  Kinda "out-of-sight out-of-mind" thing.  Don't forget to edit fstab to point to new mount point.

---

### Post by C-A on 2007-02-25
thanks for the replies, its working now that way I wanted it to

---

