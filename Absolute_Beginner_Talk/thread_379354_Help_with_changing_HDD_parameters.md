---
title: "Help with changing HDD parameters"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by baysl on 2007-03-08
When I write:

ls -la /media

I get output:

total 124
drwxr-xr-x 10 root root  4096 2007-03-08 16:31 .
drwxr-xr-x 21 root root  4096 2007-02-26 22:48 ..
[B]dr-x------  1 roko roko 28672 2007-02-26 18:25 160GB
dr-x------  1 roko roko 65536 2007-02-26 18:34 320GB[/B]
lrwxrwxrwx  1 root root     6 2007-02-26 20:08 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2007-02-26 20:08 cdrom0
dr-xr-xr-x  1 root root  4096 1999-06-19 23:12 cdrom1
lrwxrwxrwx  1 root root     7 2007-02-26 20:08 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2007-02-26 20:08 floppy0
dr-xr-xr-x  1 root root  4096 2007-03-07 21:33 hda1
drwxr-xr-x  4 roko roko  4096 2007-03-08 17:46 hda5
drwxr-xr-x  2 root root  4096 2007-02-27 00:03 windows

I want this disks:
[B]dr-x------  1 roko roko 28672 2007-02-26 18:25 160GB
dr-x------  1 roko roko 65536 2007-02-26 18:34 320GB[/B]

to be writable.

What do I write in terminal to make them writable?

---

### Post by taurus on 2007-03-08
Are they ntfs, vfat, ext3, etc.?

---

### Post by dannyboy79 on 2007-03-08
show us results from these 2 commands:

mount

sudo fdisk -l

then we can help.

---

### Post by baysl on 2007-03-08
160GB and 320GB are NTFS.

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1785    14337981    7  HPFS/NTFS
/dev/hda2            1786       10010    66067312+   f  W95 Ext'd (LBA)
/dev/hda5            1786        7394    45054261   83  Linux
/dev/hda6            7395       10010    21012988+  83  Linux

Disk /dev/sda: 320.0 GB, 320072932864 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       20023   160834716    7  HPFS/NTFS

---

### Post by dannyboy79 on 2007-03-08
and the other command?

mount

---

### Post by baysl on 2007-03-08
root@linux:~# mount
/dev/hda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type ntfs (rw,umask=222,utf8)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/320GB type ntfs (rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8)
/dev/hda5 on /media/hda5 type ext3 (rw)
/dev/sdb1 on /media/160GB type ntfs (rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8)
/dev/hdc on /media/cdrom1 type iso9660 (ro,noexec,nosuid,nodev,user=roko)

---

### Post by taurus on 2007-03-08
You know you can't write to ntfs unless you use ntfs-3g driver instead of ntfs.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by dannyboy79 on 2007-03-08
ok, well as you can see by the mount command that those are both formatted as ntfs, currently linux has write support ONLY if you install a third party driver. it has been in development and use for a very long time but some people don't trust it and will tell you that it can corrupt your hard drive data and you could lose it all. you will want to follow this thread if you would like write support for these 2 drives and mount points. 

[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)

in linux, folders are merely mount points for the partition's data, so you have designated the folder /media/320GB and /media/160GB as the mount points for the data that is located within your sda1 hard drive and sdb1 hard drive. since they have the s, I can tell that they are possible sata drives or scsi drives. this is due to them using scsi emulation in linux. (i think, some1 correct me if I am wrong) your fstab looks like you followed a guide in order to add your additional drives so could read them, I am surprised that the guide didn't specifically tell you that you can't put "rw" for a drive that is formatted with ntfs filesystem. anyway, good luck.

---

### Post by baysl on 2007-03-08
I did everything as it was writed in instructions, but I get errors:

root@linux:~# sudo fdisk -l | grep NTFS
/dev/hda1   *           1        1785    14337981    7  HPFS/NTFS
/dev/sda1               1       38913   312568641    7  HPFS/NTFS
/dev/sdb1               1       20023   160834716    7  HPFS/NTFS
root@linux:~# sudo cp /etc/fstab /etc/fstab.bak
root@linux:~# gksu gedit /etc/fstab

I writed this in /etc/fstab:
/dev/sda1 /media/320GB ntfs-3g defaults,locale=en_US.utf8 0 0

root@linux:~# sudo umount /dev/sda1
root@linux:~# sudo mount -a
Volume is scheduled for check.
Please boot into Windows TWICE, or use the 'force' mount option.

What now?

---

### Post by dannyboy79 on 2007-03-08
can't help ya as I don't use the ntfs-3g driver. why don't you go to the website for this driver as I am sure you're not the first 1 to receive this error. i found how to solve this in gogle: [http://forum.ntfs-3g.org/viewtopic.php?p=686&sid=1617194f32e19a70c53ea6b659188ec5](http://forum.ntfs-3g.org/viewtopic.php?p=686&sid=1617194f32e19a70c53ea6b659188ec5)

gogle is your friend so I would next time give that a go before posting but it's your choice as the community will be here for ya.

---

