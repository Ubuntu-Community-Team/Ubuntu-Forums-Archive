---
title: "Fsck at startup"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Penguin Power on 2008-01-08
Fsck is determined to check my NTFS partitions when Windows screws up and uncleanly unmounts them. This can take quite a bit of time with a 750GB NTFS volume and I'd like to know how to quit fsck while it is taking place, or at least be presented with the option "would you like to check the fs?" before the fsck takes place.

Is this possible?

---

### Post by newlinux on 2008-01-08
I don't know about being presented with an option about fsck'ing, but If you have that partition mounted in /etc/fstab putting a 0 in the sixth column of it's mount line and that should stop it from being fscked.

---

### Post by philinux on 2008-01-08
Fsck should not really be checking your ntfs partition.

You need to edit your fstab file.

gksudo /etc/fstab

if you take a look at mine

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9024104a-fa2f-4f85-bb6d-385637bdee48 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=0f7689c1-b451-4bc8-9120-d5b224921210 /home           ext3    defaults        0       2
# /dev/sdb1
# UUID=0B5C-1AFA  /media/sdb1     vfat   iocharset=utf8,umask=0000,rw,noexec,nosuid,nodev,sync,user 0 0

```

You''ll see my windows drive sdb1 has user 0 0 at the end the last 0 means don't fsck. Just change yours to a  0.

---

### Post by Hospadar on 2008-01-08
Also too, if you are annoyed by those regular checks of your main drive (the ones that are like "your drive has been mounted 30 times without being checked") you can use the command "tune2fs" (do "man tune2fs" to figure how to use it)

you could also change your fstab so your windows drives arn't mounted at boot time if you don't access them ttoo frequently from linux.  (I'm not sure what the option is to do this, maybe noauto? I'm sure you could track it down though)

---

### Post by dcstar on 2008-01-08
> **Penguin Power said:**
> Fsck is determined to check my NTFS partitions when Windows screws up and uncleanly unmounts them. This can take quite a bit of time with a 750GB NTFS volume and I'd like to know how to quit fsck while it is taking place, or at least be presented with the option "would you like to check the fs?" before the fsck takes place.

Is this possible?

Someone has written a script to do what you are asking for, do a forum search and you should find it.

---

