---
title: "Problems with ntfs-3g and raid 5."
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by gu014 on 2007-02-15
Hello,
I am trying to recover some information from a ntfs raid 5. I am trying to recover this using an Ubuntu 6.10 Live CD

I have installed the ntfs-3g and my /etc/fstab:
```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0


/dev/cciss/c0d0 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0

```

When i then try to do a mount -a it yields:
```
sudo mount -a
NTFS signature is missing.
Failed to startup volume: Invalid argument
Failed to mount '/dev/cciss/c0d0': Invalid argument
The device '/dev/cciss/c0d0' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

Am i doing anything incorrectly? I apologize for being a n00b but i am hoping for any suggestions.  Thank you.

---

### Post by givré on 2007-02-15
> **gu014 said:**
> 
```


/dev/cciss/c0d0 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0

```

When i then try to do a mount -a it yields:
```
sudo mount -a
NTFS signature is missing.
Failed to startup volume: Invalid argument
Failed to mount '/dev/cciss/c0d0': Invalid argument
The device '/dev/cciss/c0d0' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```
Are you sure for your /dev/cciss/c0d0
What give you :```

sudo fdisk -l
```

---

