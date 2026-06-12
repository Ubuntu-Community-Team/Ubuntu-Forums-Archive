---
title: "Permanent access to USB drive"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by DavidNW on 2006-12-13
Hi, all.

Just having a little trouble in getting my USB drive to stay 'useable' in Ubuntu (KDE ).  I can set a mount point for it in disk management (see screenshots for information) - it is then fully accessable.  I have full read and write permissions as you can see.   

However, if I power the PC off or reboot - I lose the access to the drive.  I'm certain that this is due to the fact that my etc/fstab file has no line relating to the said drive.

I have tinkered around with the file to try to edit it, but no luck.  Does anyone know how to edit the file please.

Here's Kate's output for further information:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


Cheers,

David.

---

### Post by taurus on 2006-12-13
Add this line to your /etc/fstab...

```

/dev/sda5  /media/sda5  vfat  iocharset=utf8,umask=000  0  0

```

---

### Post by DavidNW on 2006-12-13
Thanks for your help.  However, it did not work.  Here's acouple of screenshots for further information.

---

### Post by taurus on 2006-12-13
Do you have a blank line at the end of /etc/fstab?

What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by DavidNW on 2006-12-13
This is the output from sudo fdisk -l  :

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         764     6136798+  83  Linux
/dev/hda2             765        4998    34009605    5  Extended
/dev/hda5             765         904     1124518+  82  Linux swap / Solaris
/dev/hda6             905        4998    32885023+  83  Linux

Disk /dev/hdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9538    76613953+  83  Linux
/dev/hdb2            9539        9726     1510110    5  Extended
/dev/hdb5            9539        9726     1510078+  82  Linux swap / Solaris

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           2        4864    39062047+   5  Extended
/dev/sda5               2        4864    39062016    7  HPFS/NTFS
[root@localhost david]#      

........................................................................

The last line in etc/fstab is the code you gave me:

/dev/sda5  /media/sda5  vfat  iocharset=utf8,umask=000  0  0

This is really weird.  I have just booted over into Mandriva and the output via Kate is completely different from the Kate output in Unbuntu!  Here it is:

# This file is edited by fstab-sync - see 'man fstab-sync' for details
/dev/hda1 / ext3 defaults 1 1
/dev/hda6 /home ext3 defaults 1 2
/dev/hdc /mnt/cdrom auto umask=0,user,iocharset=iso8859-15,codepage=850,noauto,ro,exec,users 0 0
/dev/hdd /mnt/cdrom2 auto umask=0,user,iocharset=iso8859-15,codepage=850,noauto,ro,exec,users 0 0
none /mnt/floppy supermount dev=/dev/fd0,fs=ext2:vfat,--,umask=0,iocharset=iso8859-15,sync,codepage=850 0 0
none /proc proc defaults 0 0
/dev/hda5 swap swap defaults 0 0
/dev/hdb5 swap swap defaults 0 0
/dev/sda5               /mnt/removable          ext3    pamconsole,exec,noauto,managed 0 0
....................................................................

I can fully access the USB drive here (I'm in Mandriva now), and I can fully access it in Ubuntu if I use the GNOME desktop - but not if I use KDE 3.4  I'm at a loss to understand why that should be.

I suppose I should not complain, as it's only KDE that won't allow access for some strange reason.

Thanks very much for your help.

David

---

