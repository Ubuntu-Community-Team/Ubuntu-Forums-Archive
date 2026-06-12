---
title: "external hard drive"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by mrpaulAU on 2007-12-07
I recently reformatted my hard drive on my pc. I got fed up with windows and installed ubuntu. When I try to connect to my external hard drive that is full of my music and movies and stuff, ubuntu won't mount the drive. The drive is in ntfs format so I tried to install ntfs-3g and fuse. I was finally able to do that and synaptic says that they're installed. I still cannot access my drive. Any help would be appreciated. Thanks,

---

### Post by taurus on 2007-12-07
What are the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by mrpaulAU on 2007-12-07
paul@paul-desktop:~$ sudo fdisk -l
[sudo] password for paul:

Disk /dev/sda: 60.0 GB, 60000000000 bytes
255 heads, 63 sectors/track, 7294 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6991    56155176   83  Linux
/dev/sda2            6992        7294     2433847+   5  Extended
/dev/sda5            6992        7294     2433816   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7451035d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS
paul@paul-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=677c16fc-e707-4f20-9c01-bff4850cbd03 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=38a3c735-d5d5-4ed0-adde-6ac5ea14c9b1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
paul@paul-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              53G  2.1G   48G   5% /
varrun                506M   88K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   84K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/scd0             481M  481M     0 100% /media/cdrom0

---

### Post by taurus on 2007-12-07
Try

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
ls -la /media/sdb1
```

---

### Post by jonny5tails on 2007-12-07
Have you tried unplugging & replugging it back in? Simple, but it works for my WD Passport.

---

### Post by Mad_Dawg on 2007-12-07
I have a USB external that I plug in before I turn the computer on.  It has worked flawlessly.

---

### Post by mrpaulAU on 2007-12-09
I tried unplugging it and plugging it back in. I tried to have it running before I turned on my computer. I tried the code you gave me as well. This is what I got from the code.

paul@paul-desktop:~$ sudo apt-get update
[sudo] password for paul:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Translation-en_US      
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Fetched 2B in 0s (3B/s)  
Reading package lists... Done
paul@paul-desktop:~$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
paul@paul-desktop:~$ sudo mkdir /media/sdbl
mkdir: cannot create directory `/media/sdbl': File exists
paul@paul-desktop:~$ sudo mount -t ntfs-3g dev/sdbl /media/sdbl
ntfs-3g: Cannot mount 'dev/sdbl': No such file or directory

ntfs-3g 1.913 - Third Generation NTFS Driver

Copyright (C) 2005-2006 Yura Pakhuchiy
Copyright (C) 2006-2007 Szabolcs Szakacsits

Usage:    ntfs-3g <device|image_file> <mount_point> [-o option[,...]]

Options:  ro, force, locale=, uid=, gid=, umask=, fmask=, dmask=,
          streams_interface=. Please see details in the manual.

Example:  ntfs-3g /dev/sda1 /mnt/win -o force,locale=en_EN.UTF-8

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)
paul@paul-desktop:~$ ls -la /media/sdbl
total 8
drwxr-xr-x 2 root root 4096 2007-12-09 09:53 .
drwxr-xr-x 6 root root 4096 2007-12-09 10:00 ..

Any more help would still be appreciated. I would hate to have to go back to windows. Thanks.

---

### Post by taurus on 2007-12-09
That is number 1, _not_ a letter l!

---

### Post by viking777 on 2007-12-09
Its very very simple. At least it was for me but then I use KDE. If you use Gnome or if your problem is different from mine it might not be so simple.

Anyway this is what I did. Plug in your drive and hopefully you have an icon on your desktop for it. Right click the icon select 'Properties' and you should (will if you use kde) see a tab called 'mounting'. Select this tab and you will see a check box called 'mount as user' (on gnome I have no idea what you will get) anyway if you see this checkbox then click in it to remove the 'x' from it.

Your drive will now work normally.

Easy peasy and no crappy command line:):)

---

### Post by CaptainInsaneO on 2007-12-09
<dumb question>
Did you configure ntfs-3g after you installed it?
</dumb question>

---

### Post by mrpaulAU on 2007-12-13
Still not working. I have not configured ntfs-3g, what do I have to do for that? Also, this is the output from writing in the code with the _1_. 

paul@paul-desktop:~$ sudo mkdir /media/sdb1
mkdir: cannot create directory `/media/sdb1': File exists
paul@paul-desktop:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/sdb1 ntfs-3g defaults,force 0 0

paul@paul-desktop:~$ ls -1a /media/sdb1
.
..

Thanks again for the help!

---

### Post by CaptainInsaneO on 2007-12-13
Go into Add/Remove and search for NTFS. It will bring up the ntfs config tool. Use that.

---

