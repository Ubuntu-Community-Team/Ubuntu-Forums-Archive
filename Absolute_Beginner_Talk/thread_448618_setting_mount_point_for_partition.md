---
title: "setting mount point for partition"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by sailingboarder on 2007-05-19
right now i have a system with three partitions
a 40 gb ntfs partition for windows
a 10 gb ext3 partition for ubuntu
and a 100 gb fat32 partition to share files between the two
i recently reformatted the fat32 partition cause it had become corrupted
the new partition shows up on windows, but is not mounted in ubuntu
how do i set the mount point for the partition without having to go through the installation process?

---

### Post by taurus on 2007-05-19
Can you post both of these outputs?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by sailingboarder on 2007-05-19
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5100    40965718+   7  HPFS/NTFS
/dev/sda2            5101        6375    10241437+  83  Linux
/dev/sda3            6376        6630     2048287+  82  Linux swap / Solaris
/dev/sda4            6631       19457   103032877+   b  W95 FAT32
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=6777a761-e220-476e-ae7d-7d6468927f4f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=4598-29C9  /share          vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=D0782DE7782DCCD2 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=6624f370-2ec9-4219-b492-dbef42422c76 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by Outrunner on 2007-05-19
Looks like it's mounted on /share. If you can't find that directory then try

```
sudo mount -a
```

To mount everything that appears in /etc/fstab (which inclundes you're FAT32 partition aswell)

---

### Post by taurus on 2007-05-19
If you reformatted /dev/sda4, the UUID has been changed so you can either find the new UUID or edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace this line

```
UUID=4598-29C9  /share          vfat    defaults,utf8,umask=007,gid=46 0       1
```
with this one.

```
/dev/sda4     /share          vfat    defaults,utf8,umask=007,gid=46 0       1
```
Save it and reboot.

Now, see if /de/sda4 is mounted to /share.

```
df -h
```

---

### Post by sailingboarder on 2007-05-19
neither solution worked
```
sailingboarder@laptop:~$ sudo mount -a
Password:
mount: mount point /share does not exist
sailingboarder@laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.7G  9.2G  8.1M 100% /
varrun                502M  108K  501M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb            502M   96K  501M   1% /proc/bus/usb
udev                  502M   96K  501M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   33M  469M   7% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1              40G   29G   11G  75% /windows

```

---

### Post by sailingboarder on 2007-05-19
ok, i figured it out
i made a folder using ```
sudo mkdir share
``` then i mounted everything using ```
sudo mount -a
```
now everything works

---

