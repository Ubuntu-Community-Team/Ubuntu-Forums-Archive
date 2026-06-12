---
title: "uuid in fstab problems"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by thor918 on 2007-01-28
Hi there. I got a hotswap serial disk card. where new disks can be inserted or removed.

if I use /dev/sd* in fstab the static info in that file can be uncorrect if I put a new harddrive into the machine. The /dev/sd* can change names.
so to correct this I want to use UUID in fstab.

Problem is that some of the UUID's give errors....

from /etc/fstab:
# /dev/sda --
UUID=d6ddc83d-d671-4c5a-9a90-2f6189664712       /disks/hd4               ext3    defaults,errors=remount-ro,acl 0       1

# /dev/sdb -- 
UUID=c4e0ea4c-1806-468e-85fa-1730632e4ee5       /disks/hd5               ext3    defaults,errors=remount-ro,acl 0       1

Output when I try to mount fstab:
 root@ubuntu:~# mount -a
 mount: special device UUID=c4e0ea4c-1806-468e-85fa-1730632e4ee5 does not exist

/dev/sda will mount perfectly, but it will not work on sdb!

if I change fstab to use /dev/sdb instead of uuid it works perfectly


root@ubuntu:~# ls /dev/disk/by-uuid/ -alh
total 0
drwxr-xr-x 2 root root 160 2007-01-28 22:08 .
drwxr-xr-x 5 root root 100 2007-01-28 22:08 ..
lrwxrwxrwx 1 root root  10 2007-01-28 22:08 089437559437448A -> ../../hdc3
lrwxrwxrwx 1 root root   9 2007-01-28 22:08 40ba69ce-08bf-47a5-8cc4-8e5a429b0154 -> ../../hdb
lrwxrwxrwx 1 root root   9 2007-01-28 22:08 4c5b022e-9193-465a-9516-161256152a92 -> ../../hdd
lrwxrwxrwx 1 root root   9 2007-01-28 22:08 c4e0ea4c-1806-468e-85fa-1730632e4ee5 -> ../../sdb
lrwxrwxrwx 1 root root   9 2007-01-28 22:08 d6ddc83d-d671-4c5a-9a90-2f6189664712 -> ../../sda
lrwxrwxrwx 1 root root  10 2007-01-28 22:08 e184f29a-1a29-4778-a9a6-9ddb42b738d7 -> ../../hda1


/lib/udev/vol_id /dev/sdb | grep UUID
ID_FS_UUID=c4e0ea4c-1806-468e-85fa-1730632e4ee5


anyone got a clue on what's wrong???




I'm running server version of ubuntu
root@ubuntu:~# uname -a
Linux ubuntu 2.6.15-23-server #1 SMP Tue May 23 15:10:35 UTC 2006 i686 GNU/Linux

---

### Post by thor918 on 2007-01-28
strange!

If I change how I put the uuid in fstab to like this:
/dev/disk/by-uuid/c4e0ea4c-1806-468e-85fa-1730632e4ee5       /disks/hd5               ext3    defaults,errors=remount-ro,acl 0       1

it works!

---

