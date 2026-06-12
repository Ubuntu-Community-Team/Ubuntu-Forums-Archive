---
title: "changing ntfs 3g drive write permissions"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by dhawald3 on 2007-04-20
I have installed ntfs 3g
I have meny ntfs partitions on my HD

and I want to disable write access from kubuntu on some of those drives.

how do I do it??

---

### Post by Obor on 2007-04-20
You need to edit your fstab file
(replace gksudo to kdesu and gedit to kate if you are in kubuntu)
```
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
```

and change the required partitions to look like this
/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0

where /dev/hda1 is the drive and /media/windows is the mount point.

If you post output of 
```
sudo fdisk -l
gedit /etc/fstab
```

someone will tell you what to change

---

### Post by Comzee on 2007-04-20
If you go Applications->System tools->NTFS configuration tool, you can make it so all internal NTFS partitions are disabled for write. I don't know how to disable selective ones though.

---

