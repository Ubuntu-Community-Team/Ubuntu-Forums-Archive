---
title: "Cannot Unmount cd or dvd drives"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by joshgtv6 on 2006-10-30
hey guys, i'm having another problem that just started.  I haven't made any changes to the system so some help would be great.  

When I insert a cd or dvd into one of my drives I have to manually mount it which is new but not really an issue.  The problem is i can't eject them or unmount them.  This is the error i'm recieving. 

umount: /dev/hdc mount disagrees with the fstab
eject: unmount of `/tmp/disks-conf-hdc' failed 


here is what my fstab looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /media        ext3    defaults 0 2

Here is what my fdisk looks like if you need this as well

Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4770    38314993+  83  Linux
/dev/hda2            4771        4863      747022+   5  Extended
/dev/hda5            4771        4863      746991   82  Linux swap / Solaris

Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       36481   293033601   83  Linux


Anyone have any ideas?

---

### Post by tatimmer on 2006-10-30
I have resorted to writting a script which I use to mount/unmount my floppy, pendrive and datacd devices.  It uses pmount.  Remove all references to these devices in fstab.  The script is on my website.  It works first time every time for me where automount failed after awhile (gnome-volume-manager problem I think).

---

### Post by joshgtv6 on 2006-10-30
i appreciate the help and suggestion. It was working fine and then all of a sudden it stopped working the way it's supposed to.  This is becoming a daily thing.  I'll keep using Ubuntu for another month or so and if things keep breaking for no apparent reason then it's gone.

---

