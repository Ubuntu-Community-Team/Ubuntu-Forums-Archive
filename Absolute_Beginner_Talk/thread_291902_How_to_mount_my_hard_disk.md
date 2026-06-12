---
title: "How to mount my hard disk"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by leopard6661 on 2006-11-03
How do I mount my windows hard disk on xubuntu, I connected it but can read it from linux using thunar file manager, is there a way to mount it via commands
thanx

---

### Post by Kateikyoushi on 2006-11-03
You can list your partitions with this command.

```
sudo fdisk -l
```

Make a folder where you can mount the windows partition, backup and edit your fstab.
```
sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
```

Add this line to the end but replace hdXX with your windows partition, it is most likely NTFS possibly fat in that case replace ntfs with vfat.
```
/dev/hdXX    /media/windows ntfs  nls=utf8,umask=0222 0    0
```

---

### Post by justifier on 2006-11-03
you can temporarily mount by 

code:
sudo mkdir <direcory to mount to>
sudo mount -t <filesystem> /dev/hdaXX /directory/you/made

or read man mount

---

