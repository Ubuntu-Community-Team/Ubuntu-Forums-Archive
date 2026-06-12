---
title: "[SOLVED] mount ntfs-3g"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by duruttye on 2007-09-30
sudo ntfs-3g /dev/hda5
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/hda5': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.

I got rid of the windows, because it, broke, of course, so what now??

---

### Post by Pumalite on 2007-09-30
Post:
sudo fdisk -lu
cat /etc/fstab

---

### Post by bsharp on 2007-09-30
I think your post answers your own question, since you don't have Windows anymore and you obviously can't boot into it to shutdown it cleanly, try one of the other options like running ntfsfix version 1.13.1 unless your Windows install was Vista or just mount it in read-only mode.

---

### Post by duruttye on 2007-09-30
Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2              63   398267414   199133676    f  W95 Ext'd (LBA)
/dev/hda5        20482938   225279494   102398278+   7  HPFS/NTFS
/dev/hda6       225279558   307194929    40957686    7  HPFS/NTFS
/dev/hda7       307194993   398267414    45536211    7  HPFS/NTFS
/dev/hda8             189    17575109     8787460+  83  Linux
/dev/hda9        17575173    20482874     1453851   82  Linux swap / Solaris

Partition table entries are not in disk order

FSTAB:

proc /proc proc defaults 0 0
# Entry for /dev/hda8 :
UUID=5c7b0244-dc26-4081-8a76-c288209098dc / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=94F45025F4500BBC /media/hda5 ntfs umask=222,utf8 0 0
# Entry for /dev/hda6 :
UUID=FCC0863BC085FBE0 /media/hda6 ntfs umask=222,utf8 0 0
# Entry for /dev/hda7 :
UUID=FEEC3E74EC3E26F5 /media/hda7 ntfs umask=222,utf8 0 0
# Entry for /dev/hda9 :
UUID=4e195296-f244-44d8-b153-508d75f632a9 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hda5 /media/behemot ntfs umask=0222 0 0
/dev/hda6 /media/camptwins ntfs umask=0222 0 0
/dev/hda7 /media/simpsons ntfs umask=0222 0 0

---

### Post by duruttye on 2007-09-30
> **bsharp said:**
> I think your post answers your own question, since you don't have Windows anymore and you obviously can't boot into it to shutdown it cleanly, try one of the other options like running ntfsfix version 1.13.1 unless your Windows install was Vista or just mount it in read-only mode.

I know that I don't have Windows anymore...
and I wanna have write permission too :)

---

### Post by duruttye on 2007-09-30
I'm trying to install ntfs-3g again, this is the error I get:


config.status: executing depfiles commands
****************************************************************************
* WARNING  WARNING  WARNING  WARNING  WARNING  WARNING  WARNING  WARNING   *
* The FUSE user space binaries were NOT installed with root directory      *
* executable prefix. This means that automounting NTFS volumes during boot *
* could fail. This can be fixed the below way by reinstalling FUSE using   *
* the right 'configure' option during FUSE compilation:                    *
*       ./configure --exec-prefix=/                                        *
*       make && sudo make install                                          *
* WARNING  WARNING  WARNING  WARNING  WARNING  WARNING  WARNING  WARNING   *
****************************************************************************
You can type now 'make' to build ntfs-3g.

Is it a serious one? or should I continue with the installation?
thanx :)

---

### Post by duruttye on 2007-09-30
Hey guys!

The problem solved, the ntfs-config package was broken.

The command for mounting these former windows drives is :

 sudo mount -t ntfs-3g /dev/hdaX /where/to/mount -o force

I did it all by myself hehe
:guitar:

---

