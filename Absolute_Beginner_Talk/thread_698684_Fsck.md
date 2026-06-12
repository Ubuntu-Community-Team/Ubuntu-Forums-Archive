---
title: "Fsck"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by skymera on 2008-02-16
when i start ubuntu it always disk checks, always saying its errored.

im in the LiveCD now and i think this is best to check the disk, how do i do a full scan for errors?

---

### Post by taurus on 2008-02-16
```
sudo fsck -y /dev/sda1
```
Assuming /dev/sda1 is the partition you want to check.  Remember, don't use fsck with ntfs or vfat filesystem.

And if you do a normal shutdown instead of pushing the power, then there is something with your harddrive if you keep getting error messages with fsck.

---

### Post by wolfen69 on 2008-02-16
become root
```
sudo su
```
make sure drive is unmounted.
```
umount /dev/sda1
```
insert your drive for sda1
then
```
fsck /dev/dsa1
```

---

