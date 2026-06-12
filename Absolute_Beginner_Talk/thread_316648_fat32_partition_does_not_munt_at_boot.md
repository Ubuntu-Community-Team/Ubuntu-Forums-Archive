---
title: "fat32 partition does not munt at boot"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by aridus on 2006-12-11
Could anybody advise me with this? I have a Fat32 drive that used to be mounted automatically (sda5 in the current fstab file - see below) but after I formatted it recently it is not mounted automatically at boot and I cannot understand why (and I don't know how to mount it after boot either). With grateful thanks for any help!

Here is fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4 -- converted during upgrade to edgy
UUID=fb2fb857-3e3b-4c19-ad0c-53fe8d53f7bc / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=07D5-080C /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda2 -- converted during upgrade to edgy
UUID=32A402D6A4029D0B /media/sda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=443A-4D95 /media/sda5 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda6 -- converted during upgrade to edgy
UUID=129261fc-0d0a-4be7-8cc8-dc638114563a none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by housam on 2006-12-11
Try to read [this link]("http://doc.gwos.org/index.php/DapperGuide#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only")

---

### Post by taurus on 2006-12-11
I would make the entry for /dev/sda5 to look something like this!

```

/dev/sda5   /media/sda5   vfat   iocharset=utf8,umask=000  0  0

```

---

