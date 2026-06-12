---
title: "More problems with UUID and swap"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by kexodusc on 2007-02-18
Hi all, more problems with my swap - don't have any apparently.

Here's my fdisk -l
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1305    10482381   83  Linux
/dev/hdb2            7170        7476     2465977+  82  Linux swap / Solaris
/dev/hdb3            1306        3916    20972857+  83  Linux
/dev/hdb4            3917        7169    26129722+  83  Linux

My fstab looks like:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=0430cb1b-d87c-4aaf-a0f7-c747424f35d9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb3
UUID=d92e80be-b567-48b7-81a5-e9e18b6754e7 /home           ext3    defaults        0       2
# /dev/hdb4
UUID=4c896234-883e-4c9a-bef4-7097e220740e /kubuntu        ext3    defaults        0       2
# /dev/sda1
UUID=E294AD75FC4162F5 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=009ef88a-2192-4ba1-bcaa-234b50d03adc   none   swap   sw   0   0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

I ran a "ls /dev/disk/by-uuid/ -alh" and get:
drwxr-xr-x 2 root root 140 2007-02-18 08:22 .
drwxr-xr-x 6 root root 120 2007-02-18 08:22 ..
lrwxrwxrwx 1 root root  10 2007-02-18 08:22 009ef88a-2192-4ba1-bcaa-234b50d03adc -> ../../hdb2
lrwxrwxrwx 1 root root  10 2007-02-18 08:22 0430cb1b-d87c-4aaf-a0f7-c747424f35d9 -> ../../hdb1
lrwxrwxrwx 1 root root  10 2007-02-18 08:22 4c896234-883e-4c9a-bef4-7097e220740e -> ../../hdb4
lrwxrwxrwx 1 root root  10 2007-02-18 08:22 d92e80be-b567-48b7-81a5-e9e18b6754e7 -> ../../hdb3
lrwxrwxrwx 1 root root  10 2007-02-18 08:22 E294AD75FC4162F5 -> ../../sda1



A bit hard on the eyes, but my UUID appears right - why then, when I try a swapon -a do I get the following message?
swapon: /dev/disk/by-uuid/009ef88a-2192-4ba1-bcaa-234b50d03adc: Invalid argument

I understand swap space isn't critical with adequate RAM, but I'd like to have this working...any ideas?

---

### Post by mcduck on 2007-02-18
try running 'sudo mkswap /dev/hdb2' and then again 'sudo swapon -a'. Then post the output of 'free -m' here :)

---

### Post by kexodusc on 2007-02-18
> **mcduck said:**
> try running 'sudo mkswap /dev/hdb2' and then again 'sudo swapon -a'. Then post the output of 'free -m' here :)

Ugh...that did it...mkswap - I've actually done that before, shoulda known!  Thanks McDuck

Free -m:

 total       used       free     shared    buffers     cached
Mem:          1011        831        179          0        166        345
-/+ buffers/cache:        319        691
Swap:         2408          0       2408


Now, would I have a new UUID and should I edit fstab to account for this?

---

### Post by taurus on 2007-02-18
You better or it will not be used again the next time you boot.  On the other hand, why not replace it with /dev/hdb2.  Then, you don't have to worry about UUID anymore.

---

