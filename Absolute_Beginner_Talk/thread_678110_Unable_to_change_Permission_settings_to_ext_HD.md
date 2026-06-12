---
title: "Unable to change Permission settings to ext HD"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Takuhari on 2008-01-25
I have a LACIE 500g hd and i cant change the permission settings to write on it....
It useto work beforehand... but i dont know what happened>_<

I am running ubuntu 6.06 and need to back up my files...



   Herez what i am getting when i am trying to change the permission settingz
> 
root@CrazyTacoCafeteria:/home/takuhari# cd ../../../media/
root@CrazyTacoCafeteria:/media# ls
LACIE  cdrom  cdrom0
root@CrazyTacoCafeteria:/media# ls -l
&#54633;&#44228; 36
dr-x------ 1 takuhari takuhari 32768 2008-01-16 00:54 LACIE
lrwxrwxrwx 1 root     root         6 2006-10-31 10:18 cdrom -> cdrom0
drwxr-xr-x 2 root     root      4096 2006-10-31 10:18 cdrom0
root@CrazyTacoCafeteria:/media# chmod 777 LACIE
chmod: changing permissions of `LACIE': Read-only file system

---

### Post by taurus on 2008-01-25
Is LACIE an ntfs filesystem?  If it is and you want to write to it, you need to install ntfs-3g driver and use it to mount your ntfs partition then.

---

### Post by gvartser on 2008-01-25
If not ntfs:

1) Check what permissions it is mounted with & what device the USB is attached to:

```
#) mount
```

(take notice of the device_path, mount_path and fs_type, need it later)
 
2) Un mount the USB disk
(make sure that no one is using the disk, it tricky to un mount then)
```
sudo umount <device_path>
```

3) Then remount it with some parameters:

```
sudo mount -t <fs_type> - o users,umask=1000,rw,noauto <device_path> <mount_path>
```

/g

---

### Post by bwhite82 on 2008-01-25
Try:

> sudo chown username LACIE

---

