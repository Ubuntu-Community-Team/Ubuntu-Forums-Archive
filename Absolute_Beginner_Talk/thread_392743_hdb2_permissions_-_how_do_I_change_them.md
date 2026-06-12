---
title: "hdb2 permissions - how do I change them"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by oddcarout on 2007-03-24
I want to store files in the second partition of my hard drive. It does not have the users permissions set to write. I was in a terminal window using the sudo_root and chmod.

chmod 773 /dev/hdb2

but it wont change. I don't know if there is a differnt way to do it for partitions vs. files.

Thanks,
Z

---

### Post by taurus on 2007-03-24
What format is /dev/hdb2 and where do you mount it?  You need to change the permissions of the mount point, not the device itself.

```
cat /etc/fstab
sudo fdisk -l
df -h
```

---

### Post by oddcarout on 2007-03-24
ok the mount point is /media/hdb2 but when I use

sudo -i
chmod 777 /media/hdb2

nothing happens, I still can't move files to this partition. I have created a folder for my picture files and can't move them there.

thanks
Z

---

### Post by taurus on 2007-03-24
What filesystem (vfat, ntfs, ext2, ext3, etc.) is /dev/hdb2?

```
sudo fdisk -l
```

---

### Post by oddcarout on 2007-03-24
ext3, linux

thanks,
z

---

