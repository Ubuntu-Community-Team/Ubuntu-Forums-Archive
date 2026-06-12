---
title: "drive permissions and mount options"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by nonlinear on 2007-05-15
i know there are 507458437 threads about this, but i've read through many and haven't been able to resolve my question.  

I have an NTFS drive (sda1), an ext3 (sda7) drive, swap, and two vfat drives (sda6 & sda8).  The NTFS and one vfat drive (sda1 & sda8) are mounted on boot, but one of the vfat drives (sda6) isn't mounted.  I want to have all three of these drives mounted.  Reading throuhg the forums, the common way to change permissions in order to mount seems to be to set the entry in fstab from "umask=007" to '-o umask=oooo'

However, when i look at fstab, it appears to me that sda8 and sda6 have all of the same attributes... but when i enter 'mount' command, i can see that there are differences there.    can anyone tell me what is going on here, and what would be the best way to mount these drives (i.e. change mount or fstab).  also, what is the best way to change the NTFS permissions to read only?

thanks for your help :) 

**relevant part of fstab:**
# /dev/sda7
UUID=2a5dda75-a57a-4007-85bf-e91659868a60 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=A6E033C5E0339A8F /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=CEEE-A9AE  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=AE30-E79B  /media/sda8     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=cd5ff311-0b7a-4d46-a85e-a514b1fb5cc7 none            swap    sw              0       0
[B]
fdisk:[/B]
Disk /dev/sda: 99.8 GB, 99830223360 bytes
255 heads, 63 sectors/track, 12137 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10490413+   7  HPFS/NTFS
/dev/sda2            1307       12137    87000007+   f  W95 Ext'd (LBA)
/dev/sda5            1307        1502     1574338+  82  Linux swap / Solaris
/dev/sda6            1503        2912    11325793+   b  W95 FAT32
/dev/sda7            2913        4024     8932108+  83  Linux
/dev/sda8            4025       12137    65167641    b  W95 FAT32
[B]
df -h:[/B]
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             8.4G  2.8G  5.2G  35% /
varrun                756M  104K  756M   1% /var/run
varlock               756M     0  756M   0% /var/lock
procbususb            756M  148K  756M   1% /proc/bus/usb
udev                  756M  148K  756M   1% /dev
devshm                756M     0  756M   0% /dev/shm
lrm                   756M   33M  723M   5% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1              11G  7.5G  2.6G  75% /media/sda1
/dev/sda8              63G   20G   43G  31% /media/sda8
/dev/scd0              70M   70M     0 100% /media/cdrom0
/dev/sda6              11G  6.7G  4.2G  62% /media/Resource



**id:**
uid=1000(sean) gid=1000(sean) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(sean)

**mount:**
/dev/sda7 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda8 on /media/sda8 type vfat (rw,utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=sean)
/dev/sda6 on /media/Resource type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

---

### Post by vtel57 on 2007-05-15
Incorrect posting. Author deleted. Misunderstood original poster's question.

---

