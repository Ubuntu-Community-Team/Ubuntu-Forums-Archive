---
title: "How do I access a 2nd drive in Ubuntu Dapper?"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by mister_p_1998 on 2006-05-10
Ok I installed the drive, mounted it, entered it in FSTAB, but I cant access the drive as a normal user, I can create a folder as root, but cant see it in places. What am I doing wrong? Does linux mount all drives as a virtual volume?
Thanks
Steve

---

### Post by hw-tph on 2006-05-10
Everything in Linux is mounted somewhere under the root filesystem - /. Where have you mounted your partition? It won't show up in places, when mounted a partition is just as any other directory.

You can specify the options "user" and "users" in fstab to make the partition mountable by any user on the system.

What filesystem does it use? Different filesystems have different mount options. With vfat partitions it is possible to force the owner uid and gid, which may come in handy.


Håkan

---

### Post by Borniet on 2006-05-10
Maybe paste your fstab file here, it will give us alot more to talk about. That way we can see where it is mounted, what filesystem it is, and how it is mounted.

---

### Post by mister_p_1998 on 2006-05-10
OK here you go...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdd1	/mnt/drive2	ext3	defaults	0	0

---

