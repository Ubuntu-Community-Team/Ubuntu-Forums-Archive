---
title: "Cannot gain rw access to my non journaled hfsplus partition"
date: 2010-04-30
forum: Apple Hardware Users
---

### Post by Fikusan on 2010-04-30
Im running in Ubuntu 9.1 and I'm trying to mount my osx disk for read write access. I know for a fact journaling is disabled, I tried mounting it via the command line and i get no complaint. I check the mount:

chris@ubuntu:~$ mount | grep sda2
/dev/sda2 on /media/Kitty_ type hfsplus (rw,nosuid,nodev,uhelper=devkit)

I dont know what the "nosuid,nodev,uhelper=devkit" part means... i tried repairing the disk using fsck.hfsplus.. no avail


also... checking the permissions i get:
chris@ubuntu:/media/Kitty_/System/Library/Extensions$ ls -l /media/
total 36
drwx------ 10 chris           chris 16384 1969-12-31 16:00 FC30-3DA9
drwxr-xr-x  2 root             root              4096 2010-04-28 11:35 Kitty
drwxrwxr-t  1 root                           80    42 2010-04-29 17:05 Kitty_

It seems to have rw access but when i try doing anything:
chris@ubuntu:/media/Kitty_/System/Library/Extensions$ sudo rm -v AppleIntelGMA950.kext
rm: cannot remove `AppleIntelGMA950.kext': Read-only file system

no avail... what's wrong?

---

