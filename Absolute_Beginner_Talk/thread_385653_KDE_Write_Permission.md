---
title: "KDE Write Permission?"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by Kittens on 2007-03-15
I'm trying to write files to a USB disk, but I don't have the write permission.

I used kdesu to try and drag and drop, but KDE dosn't prompt for the root password, so it doesn't open konkueror in root.

Why isn't kdesu working?

---

### Post by aysiu on 2007-03-16
Well, you've got three separate issues here.

First of all, to clarify, *kdesu* isn't **supposed** to ask for the root password. It asks for your user password if your user is in the administrative group (*admin* group).

Secondly, let's see what's wrong. In [the terminal](http://www.psychocats.net/ubuntu/terminal), paste in this command: ```
kdesu konqueror
``` Then copy and paste the output back to this thread, and explain anything that happens (Does it just go to the next line? Is there a password prompt of any kind? Be as specific as possible).

Lastly, the USB disk--what filesystem is it? If, for example, it's NTFS, it shouldn't have write permission by default. When you have the USB disk plugged in, post back here the output of these terminal commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by Kittens on 2007-03-18
```
kfamily@kfamily-desktop:~$ kdesu konqueror
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

It just gives me that in Konsole and then opens Konkueror. There is no password prompt or anything at all.

The USB disk is NTFS, I believe.

```
kfamily@kfamily-desktop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4664    37463548+  83  Linux
/dev/hda2            4665        4865     1614532+   5  Extended
/dev/hda3   *        4866        4866           0    e  W95 FAT16 (LBA)
/dev/hda5            4665        4865     1614501   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         775     5858968+   b  W95 FAT32
/dev/hdb2             776        5168    33211080    7  HPFS/NTFS

Disk /dev/sda: 1030 MB, 1030225920 bytes
4 heads, 3 sectors/track, 167680 cylinders
Units = cylinders of 12 * 512 = 6144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              21      167680     1005958+   6  FAT16
```

```
kfamily@kfamily-desktop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4664    37463548+  83  Linux
/dev/hda2            4665        4865     1614532+   5  Extended
/dev/hda3   *        4866        4866           0    e  W95 FAT16 (LBA)
/dev/hda5            4665        4865     1614501   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         775     5858968+   b  W95 FAT32
/dev/hdb2             776        5168    33211080    7  HPFS/NTFS

Disk /dev/sda: 1030 MB, 1030225920 bytes
4 heads, 3 sectors/track, 167680 cylinders
Units = cylinders of 12 * 512 = 6144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              21      167680     1005958+   6  FAT16
kfamily@kfamily-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
varrun                490M   84K  490M   1% /var/run
varlock               490M     0  490M   0% /var/lock
procbususb             10M  128K  9.9M   2% /proc/bus/usb
udev                   10M  128K  9.9M   2% /dev
devshm                490M     0  490M   0% /dev/shm
lrm                   490M   18M  473M   4% /lib/modules/2.6.17-11-generic/volatile
/dev/hdb2              32G   14G   19G  42% /windows
/dev/hdb1             5.6G  4.8G  870M  85% /fat_files
/dev/sda1             983M   52M  931M   6% /media/usbdisk
```

```
kfamily@kfamily-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2 /windows ntfs nls=utf8,umask=0222 0 0
/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0
# /dev/hda5
UUID=50e3d083-9d0b-4403-b973-b92e210de413 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
kfamily@kfamily-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2 /windows ntfs nls=utf8,umask=0222 0 0
/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0
# /dev/hda5
UUID=50e3d083-9d0b-4403-b973-b92e210de413 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by aysiu on 2007-03-18
I don't know why *kdesu* isn't asking you for a password, but it should, in fact, give you that terminal output and then open Konqueror with root privileges, as it appeared to do.

Based on your other terminal output, I think your USB drive is 1 GB and is FAT16 (not NTFS). It's weird that that's mounting at /media/usbdisk as read-only. You can force it to mount with other options by adding this line to the /etc/fstab: ```
/dev/sda1 /media/usbdisk vfat iocharset=utf8,umask=000 0 0
```

---

