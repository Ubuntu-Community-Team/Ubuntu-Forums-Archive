---
title: "Windows XP Partition no longer mounts"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by noorez on 2008-01-10
I am dual booting between gutsy and windows xp. I added a line in my /etc/fstab file so that the windows xp partition would automatically mount on startup. This worked for a while, but two days ago, it no longer mounted! I went in to  My Computer and tried to double click the unmounted windows xp icon and I got an error saying that I don't have permission to mount it.
Can someone help me with this problem?

---

### Post by forestpixie on 2008-01-10
can you give a bit more information - 

sudo fdisk -l
cat /etc/fstab

---

### Post by sneakyzor on 2008-01-10
that happend to me aswell, i just went back into fstab and deleted the line I had put in.  I mount manually from now on.

---

### Post by noorez on 2008-01-10
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03e103e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7464    59954548+   7  HPFS/NTFS
/dev/sda2            7465       14296    54878040   83  Linux
/dev/sda3           14297       14593     2385652+   5  Extended
/dev/sda5           14297       14593     2385621   82  Linux swap / Solaris



cat /etc/fstab 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=5fa70dba-3b4f-44f1-b49f-78ef68ebaaad /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=3454231e-8e8f-4753-b592-1d676b17e091 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

/dev/sda1 /media/disk ntfs-3g nosuid,nodev,local=en_CA.UTF-8,exec 0 0

---

### Post by Don1500 on 2008-01-10
"Windows XP Partition no longer mounts "

I thought you were happy about this.:)

Oh, it's a question! 

Ok, if you want the WXP OS on startup then you should:

CODE> sudo gedit /boot/grub/menu.lst

then edit this file to move the wXP loader to first in line. You can also adjust the delay before default time here. it is set to 10 sec but you can set it to what ever you want.

---

### Post by noorez on 2008-01-10
Thats not I meant. I'll try to explain better ??

When I start up gutsy, inorder to access the windows patition, I would have to go in to My Computer and double click the icon there and enter my password. 

I inserted a line to the /etc/fstab so that the partition would mount automatically mount. I would like it this  way since I have links to certain directories of my windows partition in gutsy.

The /etc/fstab line worked before, but all of a sudden it doesn't work?  I'm pretty sure that I havn't messed with any of the system files so what else could be wrong ?

---

### Post by houstonbofh on 2008-01-10
You will also get this error is the drive is marked "Dirty" from an improper shutdown.  Boot into Windows and run a chkdsk (which may require a reboot) on the NTFS partition.  You should then be able to mount it.  If not, it is another more uncommon problem.

---

