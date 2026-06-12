---
title: "Wainting for root file system"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by eskuge on 2007-12-30
I have installed Ubuntu Gutsy and everything worked fine until I updated ubuntu and installed mp3 support/dvd and changed the apperance some. Now it will not start normaly or in recovery mode. When i run recovery mode it hangs on "Waiting for root file system" and after 3-5min it displayes:

[I]Check root = bootarg cat dev/proc/cmdline or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by - uuid/4fdd2c89-77ab-467b-9bbb-de5fef3ff74a doesnot exist.
Dropping to shell![/I]

I have no idea why it happend or how to solve this. Any help would be great. I just hope I don't have to reinstall Ubuntu.

---

### Post by ^rooker on 2007-12-30
It sounds like your system harddisk died or got disconnected (is it external?)
(Try booting some live distro (e.g. ubuntu installer, Knoppix, etc... to check that disk)

---

### Post by eskuge on 2007-12-30
It's not an eternal drive. It's a drive with xp and ubuntu on it. XP works fine when booting from grub. I have tried to use the livecd from ubuntu and have no problems mounting the ubuntudisk from it.

---

### Post by ^rooker on 2007-12-30
hm.... puzzling.

anyway, I think you should verify that your system disk is mounted correctly:
1) Boot the ubuntu live distro
2) open your system disk and paste the contents of the file "/etc/fstab" on it here (or verify it yourself).
3) If you know the device file of your system disk's partition (e.g. "/dev/sda1"), please verify its UUID by typing:
"blkid /dev/xxx" (with xxx being your disk's device).
That should return something like this:
```
"/dev/sda1: UUID="4fdd2c89-77ab-467b-9bbb-de5fef3ff74a" SEC_TYPE="ext2" TYPE="ext3"
```

---

### Post by eskuge on 2007-12-31
**Her is my fstab info:**
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=4fdd2c89-77ab-467b-9bbb-de5fef3ff74a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=925CBD875CBD669F /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=faa61cb0-0c44-4227-9cf2-de187dc08703 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

**My uuid:**
```
/dev/sda2: UUID="4fdd2c89-77ab-467b-9bbb-de5fef3ff74a" SEC_TYPE="ext2" TYPE="ext3" 
```

---

### Post by eskuge on 2007-12-31
I am going to do a reinstall, but if anyone can see a reason for why Ubuntu would not boot from the fstab/uuid paste it would still be great. Thanks, for your help ^rooker. I will cross my fingers and hope I don't run in to the same problem again.

---

### Post by taurus on 2007-12-31
What if you modify both /boot/grub/menu.lst & /etc/fstab (from the LiveCD, of course) and replace the UUID with the old fashion /dev/sda2?  Would that enable you to boot Ubuntu again?

---

