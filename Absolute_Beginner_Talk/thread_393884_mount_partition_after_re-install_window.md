---
title: "mount partition after re-install window?"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by ghostshadow189 on 2007-03-26
hi all,
i've 4 partition :
sda1 : ntfs , to install window
sda5,sda6 : fat32 , to store my datas
sda7: ext2 , to install ubuntu

after i re-install window and grub , i cant mount sda1 , i just can mount sda5 and sda6 . when i try to mount , i got it :
```
sudo mount -a
mount: special device /dev/disk/by-uuid/12F011898B265141 does not exist
```

so how can i re-mount sda1 ?
thanx 4 all ur helps

---

### Post by eljalill on 2007-03-26
You could check the UUID of the device through typing
```

ls -l /dev/disk/by-uuid 

```
in a terminal. 

If it's wrong, you have to change it in /etc/fstab .

---

### Post by taurus on 2007-03-26
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace the UUID with the actual device name, /dev/sda1.

---

