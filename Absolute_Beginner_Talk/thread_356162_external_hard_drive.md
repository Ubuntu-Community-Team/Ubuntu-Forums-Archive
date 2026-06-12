---
title: "external hard drive"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by terapatrick on 2007-02-08
Can see my external usb hard drive but can only read and execute to it.
 Want to use it as a backup,it is also my windows backup drive NTFS.
 Donot know how to change permissions as it says I am owner.

  ERROR
  Cannot change permission as disk is read-only
/dev/sda1 on /media/SEA_DISK type ntfs (rw,nosuid,nodev,uid=1000,gid=1000,umask= 077,iocharset=utf8)

---

### Post by geco on 2007-02-08
> **terapatrick said:**
> Can see my external usb hard drive but can only read and execute to it.
 Want to use it as a backup,it is also my windows backup drive NTFS.
 Donot know how to change permissions as it says I am owner.

  ERROR
  Cannot change permission as disk is read-only
/dev/sda1 on /media/SEA_DISK type ntfs (rw,nosuid,nodev,uid=1000,gid=1000,umask= 077,iocharset=utf8)

you should instal ntfs-3g package (see also [http://www.linux-ntfs.org/](http://www.linux-ntfs.org/))
```

sudo aptitude update
sudo aptitude install ntfs-3g

```

then you should mount your driver specifying the ntfs-3g file system type

```

sudo mount -t ntfs-3g -w -U 1000 /dev/sda1 /media/SEA_DISK

```

where 1000 is your uid, you can check it with
```

id

```

byebye

---

### Post by terapatrick on 2007-02-08
**[SIZE="2"][/SIZE]**Thanks for information
  Terminal keeps saying no such partition.
   I have just copied my entire .ogg music files from the hard drive
  but cannot still write to it.

---

### Post by terapatrick on 2007-02-08
[SIZE="4"][/SIZE]Partioned hard drive in windows formed a FAT32 partition this now is seen  
  as a usbdisk and have read/write/execute permissions.

---

