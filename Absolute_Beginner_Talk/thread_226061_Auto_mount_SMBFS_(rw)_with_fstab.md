---
title: "Auto mount SMBFS (r/w) with fstab?"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by OoteR on 2006-07-30
This has turned into quite the mess, here's my etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc6       /home           ext3    defaults        0       2
/dev/hdc1       /media/hdc1     ntfs    defaults        0       0
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
//test/Main /mnt/test smbfs defaults,rw,username=l,password=l,umask=0222,  0 0


now, it will mount on boot, but it will not allow me r/w, i can only read as a non super-user.. 

what do i need to change so that I can access/read/write as a normal user?

thanks for any help!

---

### Post by spin2cool on 2006-07-30
The umask is your problem, IIRC.  The answer you're looking for is here:

[http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

