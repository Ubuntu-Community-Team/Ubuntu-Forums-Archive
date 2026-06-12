---
title: "New and Need Second Harddrive Help"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by cutiger95 on 2007-12-24
Here goes nothing.  

I have an old box that I previously had two operating systems installed on:

Ubuntu on one drive
XP on the other.

The XP died and I decided to totally convert this box over to Linux.  I decided that the smaller drive that previously had XP on it should be the main drive.

I loaded the Ubuntu install CD and installed 7.10.  It works great.  Now I want to deal with the second drive.  Here are the issues. 

I want that drive to do a couple of different duties:
1)  Shared across my house network with all my other computers.
2)  Be a media drive.  Video, Audio, Pictures.

The current problem is that it is formatted ext-3 but it will not allow me to write too it as I need to be root and don't want to do that.  

If I can get write from this PC I think I can get the networking stuff working.  Any help would be appreciated.

---

### Post by Rocket2DMn on 2007-12-24
Can you please post the output of the following commands:
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by cutiger95 on 2007-12-24
fdisk:
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x26282627

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14380   115507318+  83  Linux
/dev/sda2           14381       14946     4546395    5  Extended
/dev/sda5           14381       14946     4546363+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00f4d984

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001   83  Linux

cat /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1500e8c1-d15d-4f93-b3c7-35fdc58e40cb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1fd07261-7f81-4960-9a81-f632641a3c10 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


Hope this helps :-)

---

### Post by Rocket2DMn on 2007-12-24
It does help.  In order to mount the second hard drive correctly, you will want to add an entry to your fstab file.  To edit fstab, run
```
gksudo gedit /etc/fstab
```
then add the line
```
/dev/sdb1 /media/second ext3 defaults 0 0
```
Where I use "second" you can use whatever you want (this is the directory the drive will be  mounted at under /media).  You will also need to create the directory, then you can mount it with mount -a (which mounts everything in fstab)
```
sudo mkdir /media/second
sudo mount -a
```
You should then have the second hard drive mounted at /media/second

You may need to fiddle with permissions on the hard drive either from fstab or using chmod - see here for more details: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Once you have the drive mounted you can setup sharing - you will need to use SAMBA if you are sharing with windows computers.

---

### Post by cutiger95 on 2007-12-24
Will this keep it mounted on reboots or will I have to "sudo mount -a" each time I boot the system?

Also it still says that I do not have the right to modify as I have to be the "root"

---

### Post by Rocket2DMn on 2007-12-24
It will be mounted when the computer boots.  Please make sure that everything works right now though (and there is certainly no need to reboot for this!).

---

### Post by cutiger95 on 2007-12-24
When using "File-Manager" I am unable to write to this drive.

It is mounted and visible now.

Here is the 
sudo fdisk -l:
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x26282627

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14380   115507318+  83  Linux
/dev/sda2           14381       14946     4546395    5  Extended
/dev/sda5           14381       14946     4546363+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00f4d984

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001   83  Linux





etcfstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1500e8c1-d15d-4f93-b3c7-35fdc58e40cb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1fd07261-7f81-4960-9a81-f632641a3c10 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by Rocket2DMn on 2007-12-24
I don't see an entry to /etc/fstab for sdb1.  It should be as I posted above.  Unmount the drive first, add the fstab entry, then mount with sudo mount -a
```
sudo umount /media/second
``` (or wherever you have it mounted at).

---

### Post by cutiger95 on 2007-12-24
unmounted and redid the fstab entry.

Here is the result:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1500e8c1-d15d-4f93-b3c7-35fdc58e40cb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1fd07261-7f81-4960-9a81-f632641a3c10 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0[COLOR="Gray"]
/dev/sdb1       /media/basement ext3 defaults 0 0[/COLOR]

Still cannot edit /basement

---

### Post by Rocket2DMn on 2007-12-24
With the drive mounted, try running
```
chmod 777 /media/basement
sudo umount /media/basement
sudo mount -a
```
Otherwise you will need to fiddle around with the "defaults" part of the fstab entry until you get what works, again details can be found here: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) and here: [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) (they tell you to change ownership in this one)
Both are slightly different, but they should both work.

---

### Post by cutiger95 on 2007-12-24
Followed the links and performed all changes.  Had to reboot the system for everything to take effect. 

Now I just have to work on the sharing.  Thank you very much for the help.

Have a safe and Happy Holiday.

---

