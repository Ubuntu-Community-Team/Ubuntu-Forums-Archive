---
title: "File Permission problem"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by popocus on 2007-06-08
i just switched to ubuntu feisty fawn  but i dont have any permission to change files in any of my harddrives im an absolute n00b  this is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=8ebac9dc-a100-43fc-9eea-247d55ed4ad8 /               ext3    defaults,erro$
# /dev/sdb5
UUID=b86e00ab-9ce9-44dd-86c0-63fe61fde731 none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


----------------------------------------------------------------------------------
how can i make so that i can write and read to all drives
any help would be appreciated thank you.

---

### Post by taurus on 2007-06-08
Use sudo if you need to modify something outside your $HOME directory.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Rocket2DMn on 2007-06-08
If you have an external HD with NTFS or a partition with Windows, you can use ntfs-3g to correctly read/write from/to them.  You will have to enable writing after you download it using the NTFS Configuration Tool which can be found under Applications.

---

