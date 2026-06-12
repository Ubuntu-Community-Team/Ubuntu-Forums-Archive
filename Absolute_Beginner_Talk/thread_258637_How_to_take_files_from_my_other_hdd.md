---
title: "How to take files from my other hdd?"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-09-16
I have xp on my other 200gb hdd how to take the files i want to linux? without burn them on a cd?

---

### Post by tagra123 on 2006-09-16
> **haxer said:**
> I have xp on my other 200gb hdd how to take the files i want to linux? without burn them on a cd?

If the HDD drive is on another machine use network filesharing.

OR plug the harddrive in to the existing computer and mount it. Copy the files you need and remove the harddrive. 

[http://www.ubuntuforums.org/showthread.php?t=249920](http://www.ubuntuforums.org/showthread.php?t=249920)

---

### Post by haxer on 2006-09-16
I still got the files on this computer as i sayd i got it on my other hdd "on this computer" i ment how do i do then? its on ntsf i think

---

### Post by Xappe on 2006-09-16
you have to mount the drive.

check which drive and partition you want to mount:

```
sudo fdisk -l
```
(should be something like /dev/hda1)

create a mountpoint:
```

sudo mkdir /mnt/ntfs
sudo chown yourusername:yourusername /mnt/ntfs

```

mount it:
```
sudo mount -t ntfs -o user,umask=0222 /dev/yourdrive /mnt/ntfs
```

then you should be able to access your files in /mnt/ntfs and copy them wherever you want. you only have read access to ntfs with this method though...

---

### Post by haxer on 2006-09-16
and would it still be able to boot up as windows when i boot?

---

### Post by Xappe on 2006-09-16
yes.

if you want to have it mounted permanently
add a line similar to this in /etc/fstab (sudo gedit /etc/fstab)

```
/dev/yourdrive       /media/windows  ntfs    defaults,nls=utf8,umask=0222 0       1
```

and create the /media/windows mountpoint as I mentioned in the earlier post...

---

### Post by haxer on 2006-09-16
Ok thx

---

