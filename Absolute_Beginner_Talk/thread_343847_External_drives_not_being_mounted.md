---
title: "External drives not being mounted"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by unabatedshagie on 2007-01-22
I have a strange problem that has surfaced in the last coupe of days.

My external harddrive and dvdrom drive are not being mounted. The used to show up on the desktop when I logged in.

Now the only drives on my desktop are my 3 internal drives which are mounted via fstab, these never showed up on the desktop before.

Any ideas on how I can get my external harddrive and dvdrom to show up again?

---

### Post by housam on 2007-01-22
Try [this guide]("http://doc.gwos.org/index.php/DapperGuide#How_to_mount.2Funmount_CD.2FDVD-ROM_manually.2C_and_show_all_hidden_and_associated_files.2Ffolders")

---

### Post by 09adi09 on 2007-01-22
Try to see if the dvdrom and the external hdd are being mounted.
Do cat /etc/fstab
or /etc/mtab

Add them if they are not already there.

---

### Post by unabatedshagie on 2007-01-22
This is the contents of my fstab```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=adc1cba7-e01a-481d-abb0-5f4021f862e3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=9ad258b9-62f9-414a-86e3-e58ccc133b31 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/           /media/floppy0  auto    rw,user,noauto  0       0
#
# 80 Gig torrents drive /dev/sdb1
UUID=b72c9c61-18bb-4e17-904c-ddfb0d83cd78       /mnt/torrents   ext3    users,atime,rw,nodev,exec,suid  0       0
#
# 160 Gig media drive /dev/sdc1
UUID=d1818eaa-1a1e-48d7-94d0-ec05221b058c       /mnt/media      ext3    users,atime,rw,nodev,exec,suid  0       0
#
# 160 Gig documents drive /dev/sdd1
UUID=bb5021b9-df97-4059-b522-5da25af830b0       /mnt/documents  ext3    users,atime,rw,nodev,exec,suid  0       0
#
# /dev/hda2     /mnt/shared             vfat    users,atime,rw,nodev,noauto,exec,suid   0       0
#
#/dev/hda3      /mnt/backup     ext3            users,atime,rw,nodev,noauto,exec,suid   0       0

```and this is what I see when I cat /etc/mtab ```
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-10-386/volatile tmpfs rw 0 0
/dev/sdb1 /mnt/torrents ext3 rw,nodev 0 0
/dev/sdc1 /mnt/media ext3 rw,nodev 0 0
/dev/sdd1 /mnt/documents ext3 rw,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

``` As far as I can tell my dvd rom is in the fstab file so it should show up, however my external usb drive has never been in the fstab file at any time.

---

### Post by unabatedshagie on 2007-01-23
I've just found something out,

I have ubuntu set to auto log me in, when it does this my external drives & dvd rom drive are not mounted, however if I restart x and log back in the do get mounted.

Anyone have any ideas to why?

---

