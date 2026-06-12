---
title: "Second Hard drive permission = sticky"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by Lor Boo on 2006-12-17
Hello... 
Question, which I'm sure is easy ](*,) . 

I have 2 hard drives.

```
drinky@drinky:/home/ftp$ sudo fdisk -l Password:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19269   154778211   83  Linux
/dev/sda2           19270       19457     1510110    5  Extended
/dev/sda5           19270       19457     1510078+  82  Linux swap / Solaris

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2611    20972826    c  W95 FAT32 (LBA)
/dev/hda2   *        2612        7288    37568002+  83  Linux
/dev/hda3            7289        7476     1510110    5  Extended
/dev/hda5            7289        7476     1510078+  82  Linux swap / Solaris
drinky@drinky:/home/ftp$
```

HDA is the master - has the boot files.  
SDA is just storage.

I'm setting up an FTP server which I want working on the SDA drive.
however I can only access the drive using sudo for every single little thing.
This is causing an issue with the FTP server which doesn't have rights to
read/write - upload/download to the drive.
** want my user -[COLOR="Navy"]drinky[/COLOR]- to have rights to this drive without invoking sudo every time.** 
In turn I believe the FTP Program - gproftpd-8.2.2 - will also work fine then.

Here is my Fstab:
```

drinky@drinky:/media$ cat /etc/fstab # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /mnt/media      vfat    defaults,umask=0000   0   0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/sda1       /mnt/media/sata ext3   defaults,umask=0000   0   0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
drinky@drinky:/media$

```

Gotta go fight the good fight for xmas shopping here now.. but will be back.
Thanks for the help.

---

### Post by taurus on 2006-12-17
Your /dev/sda1 in /etc/fstab should look like this!

```
/dev/sda1       /mnt/media/sata   ext3   defaults   0   1
```
Then, just change the permission to /mnt/media/sata so everybody can write to it...

```
sudo chmod -R 777 /mnt/media/sata
```

---

### Post by Lor Boo on 2006-12-18
thank you Sir.
All is working fine now.
Thank you much.

---

### Post by gleed79 on 2008-01-29
i have the same problem which is not solved via chmod (for some bizarre reason). 

detail from 'sudo fdisk -l':

> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00059b09

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       23330   187398193+   b  W95 FAT32
/dev/sda2           23331       24321     7960207+   5  Extended
/dev/sda5           23331       24321     7960176   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x772c772c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       23330   187398193+  83  Linux
/dev/sdb2           23331       24321     7960207+   5  Extended
/dev/sdb5           23331       24321     7960176   82  Linux swap / Solaris



Now sdb is the drive with the ubuntu installation. sda1 had been formated with fat32 and is empty (and wanted for storage & talking to windows machines etc). Thing is I can only write on sda1 as root. The line in my fstab file is as follows:

> /dev/sda1       /media/hard_disc2       vfat    defaults        0       1 

and I have done 'sudo chmod -R 777 /media/hard_disc2' to try and get the permissions sorted such that:

> ls -al /media/hard_disc2/

> total 8
drwxrwxr-x 2 root root 4096 2008-01-30 16:17 .
drwxrwxr-x 5 root root 4096 2008-01-30 17:13 ..

 - but it just doesn't work. Only root can write to the drive.

any help would be much appreciated, i am lost!!

---

### Post by fenian on 2008-01-30
gleed79,you need to change the ownership of the drive do this (replace user with your username)...

> sudo chown -R  user:user   /media/hard_disc2

---

