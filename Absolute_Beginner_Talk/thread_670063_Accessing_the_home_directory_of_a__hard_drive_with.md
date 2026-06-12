---
title: "Accessing the /home directory of a  hard drive with existing data"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by jskong on 2008-01-17
Hi People,

I have a hard drive (let's call it hard_drive_0) from a computer with a failed motherboard.  I need to get important data from the /home directory of this hard drive.  I have another computer running Ubuntu.  This computer already has two hard drives (one master and one slave, with the slave drive mounted at /home2).  So, I opened up this computer and removed the slave drive.  I then put hard_drive_0 from the failed computer into the slot where the removed slave drive used to be.  I booted up the computer.  

Now, under /home2, I see the root directory of hard_drive_0.  For instance I see:
jskong@weng:/$ ls /home2
bin          dev    home3   initrd.img      media  root  tmp      
boot         etc    home4   initrd.img.old  mnt    sbin  usr
cdrom        home   home5   lib             opt    srv   var
debootstrap  home2  initrd  lost+found      proc   sys   vmlinuz

I can also see the files in the /usr/bin directory for example.  However, when I do 'ls /home2/home/', I see nothing!  What do I need to do to access the /home directory on my old hard_drive_0.  

Here are the relevant output:
jskong@weng:/$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9539    76621986   83  Linux
/dev/hda2            9540        9726     1502077+   5  Extended
/dev/hda5            9540        9726     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4255    34178256   83  Linux
/dev/hdb2            4864       12158    58597087+  83  Linux
/dev/hdb3            4256        4863     4883760   82  Linux swap / Solaris
/dev/hdb4           12159       14593    19559137+  83  Linux

Partition table entries are not in disk order

The content of fstab is:
jskong@weng:/$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /home2          ext3    defaults         0       0

The content of fstab on my old hard_drive_0 is:
jskong@weng:/$ more /home2/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=3d52ff3f-a52b-456c-bfda-3be547aff334 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=8625630e-7249-4c43-b5a8-8d4163f6defe /home ext2 defaults 0 2
# /dev/hdb1 -- converted during upgrade to edgy
UUID=85f63e0c-c7d5-4692-a259-0e2c586050e3 /home2 ext3 defaults 0 2
# /dev/hdd1 -- converted during upgrade to edgy
UUID=e45855b8-6f7a-41e4-b2c6-078ca64a31a8 /home3 ext3 defaults 0 2
# /dev/hdd3 -- converted during upgrade to edgy
UUID=2334b355-46e1-434e-b216-997656f7e555 /home4 ext3 defaults 0 2
# /dev/hdd2 -- converted during upgrade to edgy
UUID=180417d5-96e0-44e4-9a17-78dc9a92f34d /tmp ext3 defaults 0 2
# /dev/hda4 -- converted during upgrade to edgy
UUID=e8fb74bb-0603-41ed-93ad-cbba519aef71 /var ext3 defaults 0 2
# /dev/hda3 -- converted during upgrade to edgy
UUID=1db2994b-4731-477a-8353-7301c0dbe19f none swap sw 0 0
# /dev/hdc1 -- converted during upgrade to edgy
UUID=de6df80b-0b35-4fbe-a9c7-bee4a120daf4 /home5 ext3 defaults 0 2
#/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Thanx a bunch in advance!

---

### Post by lloyd_b on 2008-01-17
Try this (in a terminal window)
```
sudo mount /dev/hdb4 /home2/home
```

It looks like the /home directory on the old machine is a separate partition (hdb4), so you probably just need to mount it before you can access it.

Lloyd B.

---

### Post by jskong on 2008-01-17
Thank you so much!  Problem solved!

---

