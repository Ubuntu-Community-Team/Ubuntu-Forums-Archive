---
title: "cannot mount NTFS drives in kubuntu 7.10"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by lejuan on 2008-04-03
Using Kubuntu 7.10 as a LiveCD I can perfectly mount my pendrive with Konqueror, but when I try to mount the NTFS HDs, I get the error message:

"hal-storage-fixed-mount refused uid 999".

Is there some way to mount the NTFS drives from Konqueror or other graphical interface (not the console) in Kubuntu 7.10? If not, which is the way?

Thanks. Luis

---

### Post by sayakb on 2008-04-03
Try mounting it manually: ```
sudo mount -t ntfs-3g /dev/sda1 -o force
``` 
EDIT: replace sda1 with whatever applicable for you.

---

### Post by lejuan on 2008-04-03
No luck. The only way I have found is through the console:

```
sudo mkdir /media/disk
sudo mount /dev/sda1 /media/disk
```

It is a pity (a handicap for beginners) Kubuntu has not a graphical and easier way to proceed

---

### Post by stchman on 2008-04-03
> **lejuan said:**
> Using Kubuntu 7.10 as a LiveCD I can perfectly mount my pendrive with Konqueror, but when I try to mount the NTFS HDs, I get the error message:

"hal-storage-fixed-mount refused uid 999".

Is there some way to mount the NTFS drives from Konqueror or other graphical interface (not the console) in Kubuntu 7.10? If not, which is the way?

Thanks. Luis

You will have to force the mount.  First you need a mount point.  Lets walk through this.

Make a mount point on your desktop called ntfs_hd.
```
sudo mkdir /media/ntfs_hd
```

Now mount the filesystem.
```
sudo mount -t ntfs /dev/sda1
```

You can also install ntfs-config.

```
sudo apt-get install ntfs-config
```

This is a graphical tool for mounting NTFS drives.

---

