---
title: "Fstab help"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by habtish on 2007-10-20
Below is my fstab entry. For some reason my external USB drive (/dev/sdc1) is not getting mounted automatically. Any ideas? ```

# /etc/fstab: static file system information.
#
# <file system>     <mount point>       <type>      <options>           <dump>      <pass>
proc                /proc               proc            defaults            0           0
# /dev/sdb2
#UUID="03f1f827-6338-42e4-9224-b1ebdf86f4eb     /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb2                /                   ext3        defaults,errors=remount-ro     0       1
/dev/sda2        /media/windows    ntfs-3g       defaults,locale=en_US.utf8    0    0
/dev/sda3        /media/hda3      ntfs-3g    defaults,locale=en_US.utf8    0    0
#
/dev/sdb1        /media/hdb1      ntfs-3g    defaults,locale=en_US.utf8    0    0
#UUID=22597278-bfcc-4519-bf61-872d002be6d5 none            swap    sw              0       0
/dev/sdb3                none            swap    sw              0       0
/dev/cdrom            /media/cdrom0       udf,iso9660 user,noauto     0       0
#
#/dev/hda4   /boot   ext2   noauto,noatime   1 2

**/dev/sdc1           /media/sda1       ext3               umask=0022           0           0**
``` I know my fstab is not the cleanest... but these are changes I have been making since breezy.
Thanks~

---

### Post by Partyboi2 on 2007-10-23
Have u checked to see if all "Mount removable drives when..." are checked?

"System" > "Preferences" > "Removable Drives and Media"

---

### Post by habtish on 2007-10-24
> **Partyboi2 said:**
> Have u checked to see if all "Mount removable drives when..." are checked?

"System" > "Preferences" > "Removable Drives and Media"

Yes, the "Mount removable media when hot plugged" option is checked.

---

