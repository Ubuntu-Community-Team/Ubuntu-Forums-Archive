---
title: "Drive fails to mount"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Meson on 2007-02-25
One of my partitions is failing to mount.  hda7 is not mounted to share when my system is booted.

If I run sudo mount /dev/hda7 /share from the terminal, the drive loads fine.

The following is my /etc/fstab
```
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /share          ext3    defaults,uid=1000,gid=1000 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

This is the original line (which worked) before I modified the file to mount the drive under my account.
```
UUID=7546-154A  /share          vfat    defaults,utf8,umask=007,gid=46 0       1
```

All of the drives were originally entered with the UUID, but I changed them to make reading the file easier.  I assume the problem has something to do with the utf8 or umask=007 option.

Oh, and originally the drive was fat32 and I converted it to ext3.

---

### Post by Strider on 2007-02-25
Have you tried mounting the partition manually from the command line/console to see what the error message is?

-Mike

---

### Post by Meson on 2007-02-25
I tried this, however I'm not sure if this command is an exact reproduction of fstab line.

```
matt@matt-laptop:~$ sudo mount /dev/hda7 -o defaults,uid=1000,gid=1000
Password:
mount: wrong fs type, bad option, bad superblock on /dev/hda7,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

matt@matt-laptop:~$ 
```

---

### Post by Strider on 2007-02-27
The filesystem type is incorrect.  Are you sure you converted it to ext3?  Try using fstype of vfat and see what happens.

---

### Post by Meson on 2007-02-27
I know it's ext3 because if I only use the option defaults and don't try to give a user or group ID, everything works fine.

---

