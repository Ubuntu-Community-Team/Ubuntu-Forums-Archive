---
title: "why my 120G partition only show 40G in Ubuntu?"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by myhnet on 2007-08-03
i use Ubuntu 7.04 and my harddisk is 160G.
i assigned 4G to swap (sda2) 100M to /boot (sda1) and 36G to / (sda4).
then i assigned the rest (should be about 120G) to /data my own data directory.
and the Ubuntu installation showed it is 120G
but after my installation, i loggin the OS and use "df" command, it said it was only about 40G?
why?

by the way
the "fdisk" command and the "gparted" all show the sda5 has 120G.
here i add my /etc/fstab, /etc/mtable, the comeout of "df -H" and "fdisk -l"

/etc/fstab> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=37b8e32a-36bb-4855-8b5d-7904f3f66913 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=73da5e95-8b5b-4b97-b88c-fc68058c37f1 /boot           ext3    defaults        0       2
# /dev/sda5
UUID=e1a81a09-da2f-493c-89dd-403f2d55ce01 /data           ext3    defaults        0       2
# /dev/sda2
UUID=b70ea003-b892-41cf-b6aa-797259346303 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

/etc/mtab> /dev/sda4 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
/dev/sda1 /boot ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
none /proc/fs/vmblock/mountPoint vmblock rw 0 0
/dev/sda5 /data ext3 rw 0 0

df -H> Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda4               27G   7.3G    19G  29% /
varrun                 1.1G   275k   1.1G   1% /var/run
varlock                1.1G      0   1.1G   0% /var/lock
procbususb             1.1G    99k   1.1G   1% /proc/bus/usb
udev                   1.1G    99k   1.1G   1% /dev
devshm                 1.1G      0   1.1G   0% /dev/shm
lrm                    1.1G    35M   1.1G   4% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1              104M    34M    65M  34% /boot
/dev/sda5               42G    36G   4.1G  90% /data

fdisk -l> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14         529     4144770   82  Linux swap / Solaris
/dev/sda3            3826       19457   125564040    5  Extended
/dev/sda4             530        3825    26475120   83  Linux
/dev/sda5            3826       19457   125564008+  83  Linux

Partition table entries are not in disk order

---

### Post by apswartz on 2007-08-03
Strange. I was playing around with df on my own laptop and discovered the following about my main partition. 

Using the command df with different flags gives different results...

```

alan@dell:/etc$ df -H /dev/sda6
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda6              153G    45G   101G  31% /

alan@dell:/etc$ df -h /dev/sda6
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             143G   42G   94G  31% /

alan@dell:/etc$ df -k /dev/sda6
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6            148918488  43368210  97983665  31% /

```

The last result calculates to 142G in size.

---

### Post by str8line on 2007-09-02
Generally speaking when I set up my drive or a partition on a drive for Ubuntu I set up something like this....

Partition 1) 5 GB as / and formatted as ext3
Partition 2) 1 GB as /swap
Partition 3) remaing space as /home formatted in ext3 or xfs

Using this method I have never had any missing space on the drive or partitions and everything works like a charm.  I have even spread this out over multiple drives with no problem.  Might be worth a try using this format and see if you continue to have missing space.

---

