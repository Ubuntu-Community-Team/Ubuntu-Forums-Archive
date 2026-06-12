---
title: "why does TrueCrypt result in an error in Gparted"
date: 2014-07-20
forum: Any Other OS
---

### Post by shahin on 2014-07-20
I am trying to learn more about TrueCrypt. I am folloing a tutorial which takes a usb that with unallocated content, and puts come encrypted files in it.Here is the link: [https://help.ubuntu.com/community/TrueCrypt]("https://help.ubuntu.com/community/TrueCrypt") I think I am follwoing it correctly, and I am able to mount the device and the internal container again and see the files. But after encrypting the usb device, I am not able to mount it manually. And I see an exclamation mark in Gparted when I select the usb device. [ATTACH=CONFIG]254861[/ATTACH]Why is that? 
Here is what I see: 
```

root@kali:~# sudo fdisk -l

Disk /dev/sda: 26.8 GB, 26843545600 bytes
255 heads, 63 sectors/track, 3263 cylinders, total 52428800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000595c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    50198527    25098240   83  Linux
/dev/sda2        50200574    52426751     1113089    5  Extended
/dev/sda5        50200576    52426751     1113088   82  Linux swap / Solaris

Disk /dev/sdb: 2002 MB, 2002780160 bytes
62 heads, 62 sectors/track, 1017 cylinders, total 3911680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd52fcf5e

Disk /dev/sdb doesn't contain a valid partition table

```

I should then be able to issue:
```

sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
mount: special device /dev/sdb1 does not exist

```

I am trying to manually mount the usb.

---

### Post by slooksterpsv on 2014-07-20
You have to use TrueCrypt to mount the drive. The reason being is you'll need to type in a password to mount it and decrypt it.

---

### Post by oldos2er on 2014-07-20
Moved to Other OS/Distro Support.

---

### Post by slooksterpsv on 2014-07-20
Hmm.. Other OS/Distro? Should be Security Discussions.

---

