---
title: "External Drive Problem"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by XtremeSki2001 on 2007-01-10
I have a new [Western Digital 'My Book']("http://www.westerndigital.com/en/products/Products.asp?DriveID=224") (I have the 250GB version) that I picked up from Newegg recently, but it behaves awkwardly in Ubuntu Dapper (6.06).

When I boot, the drive shows-up on the desktop, but after a few minutes it disappears and reappears.  It continues this cycle non-stop.  Any ideas how to stop this madness?  I believe it's formatted as NTFS, but it only houses movies and songs from my Windows OS that runs from a different hard-drive.

Thanks for any help in advance!

---

### Post by geek_Man on 2007-01-10
Have you tried a different USB cable?

---

### Post by jd65pl on 2007-01-10
What software did you originally format it with (if at all) I have seen 4 WD pocket external HD mess up on windows, mac and linux and eventually dying. I dont think the supplied software is so hot.

---

### Post by XtremeSki2001 on 2007-01-10
It worked fine in Windows and it came ready to use 'Plug-and-Play'.

I don't think changing the USB cable will change anything as the drive always worked well in XP.

I didn't format the drive, it came all set to go.  The drive has never had issues in XP, so I see it as an OS issue and not a drive problem.

---

### Post by jd65pl on 2007-01-10
[**https://wiki.ubuntu.com/mountNTFSreadonly?highlight=%28mount%29%7C%28ntfs%29**]("https://wiki.ubuntu.com/mountNTFSreadonly?highlight=%28mount%29%7C%28ntfs%29")
Have you read this doc on mounting the NTFS file system?

---

### Post by XtremeSki2001 on 2007-01-10
> **jd65pl said:**
> [**https://wiki.ubuntu.com/mountNTFSreadonly?highlight=%28mount%29%7C%28ntfs%29**]("https://wiki.ubuntu.com/mountNTFSreadonly?highlight=%28mount%29%7C%28ntfs%29")
Have you read this doc on mounting the NTFS file system?

Nah, I'll give it a try, perhaps that's half the problem.

You guys sure are fast ... loving the Linux world so far.

Thanks again!  Will update later.

---

### Post by XtremeSki2001 on 2007-01-10
> **XtremeSki2001 said:**
> Nah, I'll give it a try, perhaps that's half the problem.

You guys sure are fast ... loving the Linux world so far.

Thanks again!  Will update later.

No luck ... got this error:

```
root@j-desktop:~# sudo mount /dev/hda /media/NTFS
mount: you must specify the filesystem type
```

---

### Post by Enverex on 2007-01-10
You sure it's not hda1? Anyway, I'd install ntfs-3g and use that (replace mount with ntfs-3g) which gives you damn near perfect read/write support which I've used for copying entire Windows partitions before. The message you're getting means that either the kernel doesn't have NTFS support or the drive is wrong/corrupted. So yeah, try ntfs-3g.

---

### Post by XtremeSki2001 on 2007-01-10
> **Enverex said:**
> You sure it's not hda1? Anyway, I'd install ntfs-3g and use that (replace mount with ntfs-3g) which gives you damn near perfect read/write support which I've used for copying entire Windows partitions before. The message you're getting means that either the kernel doesn't have NTFS support or the drive is wrong/corrupted. So yeah, try ntfs-3g.

I don't know what's wrong:

```

root@erich-desktop:~# sudo ntfs-3g /media/NTFS /dev/hda sudo: ntfs-3g: command not found 
```

```
root@erich-desktop:/dev# sudo ntfs-3g /media/NTFS /dev/hda1
sudo: ntfs-3g: command not found
```

```
root@erich-desktop:/dev# sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9541    76638051   83  Linux
/dev/hdb2            9542        9729     1510110    5  Extended
/dev/hdb5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    c  W95 FAT32 (LBA)
root@erich-desktop:/dev#
```

---

### Post by XtremeSki2001 on 2007-01-10
I tried doing it a different way by editing my /etc/fstab file like so:

```
/dev/hda1 /media/ ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sda1 /media/ ntfs-3g defaults,locale=en_US.utf8 0 0

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

But when I try to apply the settings, this happens:

```
root@erich-desktop:~# sudo umount -a
umount: /dev: device is busy
umount: /var/run: device is busy
umount: /: device is busy
root@erich-desktop:~# sudo mount -a
fusermount: mountpoint is not empty
fusermount: if you are sure this is safe, use the 'nonempty' mount option
Retrying mount ...
fusermount: mountpoint is not empty
fusermount: if you are sure this is safe, use the 'nonempty' mount option
Failed to mount NTFS
Unmounting /dev/hda1 ()
Failed to startup volume: Invalid argument
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
root@erich-desktop:~#
```

---

### Post by jd65pl on 2007-01-11
Are you sure its NTFS? I'm sure there is an easier way to check but I'm at work right now so not much opportunity for searching around/playing.
 
To check do
 
```
 
sudo aptitude update
sudo aptitude install gparted
gksudo gparted

```
 
You should then be able to properly determine the filesystem type. If you are trying to mount a drive as a type other than its actual type you could damage it.
 
J

---

### Post by Enverex on 2007-01-11
> **XtremeSki2001 said:**
> I don't know what's wrong:

```

root@erich-desktop:~# sudo ntfs-3g /media/NTFS /dev/hda sudo: ntfs-3g: command not found 
```

```
root@erich-desktop:/dev# sudo ntfs-3g /media/NTFS /dev/hda1
sudo: ntfs-3g: command not found
```

```
root@erich-desktop:/dev# sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9541    76638051   83  Linux
/dev/hdb2            9542        9729     1510110    5  Extended
/dev/hdb5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    c  W95 FAT32 (LBA)
root@erich-desktop:/dev#
```

Haha, you actually have to install ntfs-3g first :) It's in apt-get.

---

### Post by XtremeSki2001 on 2007-01-11
> **jd65pl said:**
> Are you sure its NTFS? I'm sure there is an easier way to check but I'm at work right now so not much opportunity for searching around/playing.
 
To check do
 
```
 
sudo aptitude update
sudo aptitude install gparted
gksudo gparted

```
 
You should then be able to properly determine the filesystem type. If you are trying to mount a drive as a type other than its actual type you could damage it.
 
J

I did the above, but I get this:

```
root@erich-desktop:~# sudo aptitude update
sudo: aptitude: command not found
root@erich-desktop:~# sudo aptitude install gparted
sudo: aptitude: command not found
root@erich-desktop:~# gksudo gparted
root@erich-desktop:~#
```

Do I need to install aptitude?  I checked "sudo fdisk -l" and it shows my external USB drive as FAT32, but my internal windows drive as NTFS.

> **Enverex said:**
> Haha, you actually have to install ntfs-3g first :) It's in apt-get.

I followed this [guide to install ntfs-3g]("http://everythingelse.wordpress.com/2006/07/19/89/").

As a result, I can see my windows 80GB drive, but can't access it ... I got a few errors:

```
root@erich-desktop:~# gksudo gparted
root@erich-desktop:~# sudo gedit /etc/apt/sources.list
root@erich-desktop:~# sudo apt-get update
Ign http://givre.cabspace.com dapper Release.gpg
Ign http://givre.cabspace.com dapper Release
Ign http://givre.cabspace.com dapper/main Packages
Get:1 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:3 http://security.ubuntu.com dapper-security Release.gpg [191B]
Ign http://givre.cabspace.com dapper/main-all Packages
Hit http://security.ubuntu.com dapper-security Release
Hit http://givre.cabspace.com dapper/main Packages
Ign http://ntfs-3g.sitesweetsite.info dapper Release.gpg
Hit http://us.archive.ubuntu.com dapper Release
Ign http://asher256-repository.tuxfamily.org dapper Release.gpg
Ign http://asher256-repository.tuxfamily.org ubuntu Release.gpg
Hit http://givre.cabspace.com dapper/main-all Packages
Hit http://security.ubuntu.com dapper-security/main Packages
Ign http://ntfs-3g.sitesweetsite.info dapper Release
Hit http://us.archive.ubuntu.com dapper-updates Release
Ign http://asher256-repository.tuxfamily.org dapper Release
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Ign http://flomertens.keo.in dapper Release.gpg
Ign http://ntfs-3g.sitesweetsite.info dapper/main Packages
Hit http://us.archive.ubuntu.com dapper/main Packages
Hit http://us.archive.ubuntu.com dapper/restricted Packages
Hit http://security.ubuntu.com dapper-security/restricted Sources
Ign http://asher256-repository.tuxfamily.org ubuntu Release
Ign http://ntfs-3g.sitesweetsite.info dapper/main-alll Packages
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://us.archive.ubuntu.com dapper-updates/main Sources
Hit http://us.archive.ubuntu.com dapper-updates/restricted Sources
Ign http://flomertens.keo.in dapper Release
Hit http://ntfs-3g.sitesweetsite.info dapper/main Packages
Ign http://asher256-repository.tuxfamily.org dapper/main Packages
Ign http://asher256-repository.tuxfamily.org dapper/dupdate Packages
Err http://ntfs-3g.sitesweetsite.info dapper/main-alll Packages
  301 Moved Permanently
Ign http://asher256-repository.tuxfamily.org dapper/french Packages
Ign http://asher256-repository.tuxfamily.org ubuntu/main Packages
Ign http://asher256-repository.tuxfamily.org ubuntu/dupdate Packages
Ign http://asher256-repository.tuxfamily.org ubuntu/french Packages
Ign http://flomertens.keo.in dapper/main Packages
Hit http://asher256-repository.tuxfamily.org dapper/main Packages
Hit http://asher256-repository.tuxfamily.org dapper/dupdate Packages
Hit http://asher256-repository.tuxfamily.org dapper/french Packages
Ign http://flomertens.keo.in dapper/main Sources
Hit http://asher256-repository.tuxfamily.org ubuntu/main Packages
Hit http://asher256-repository.tuxfamily.org ubuntu/dupdate Packages
Hit http://asher256-repository.tuxfamily.org ubuntu/french Packages
Hit http://flomertens.keo.in dapper/main Packages
Get:4 http://flomertens.keo.in dapper/main Sources [713B]
Fetched 716B in 2s (300B/s)
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main-alll/binary-i386/Packages.gz  301 Moved Permanently
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@erich-desktop:~# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  hal hal-device-manager libhal-storage1 libhal1 pmount
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 907kB of archives.
After unpacking 12.3kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libhal1 hal hal-device-manager libhal-storage1 pmount
Install these packages without verification [y/N]? y
Get:1 http://givre.cabspace.com dapper/main-all libhal1 0.5.7-1ubuntu19givre2 [158kB]
Get:2 http://givre.cabspace.com dapper/main-all hal 0.5.7-1ubuntu19givre2 [336kB]
Get:3 http://givre.cabspace.com dapper/main-all hal-device-manager 0.5.7-1ubuntu19givre2 [215kB]
Get:4 http://givre.cabspace.com dapper/main-all libhal-storage1 0.5.7-1ubuntu19givre2 [159kB]
Get:5 http://givre.cabspace.com dapper/main-all pmount 0.9.11-1ubuntu2givre8 [39.7kB]
Fetched 907kB in 3s (299kB/s)
(Reading database ... 72503 files and directories currently installed.)
Preparing to replace libhal1 0.5.7-1ubuntu18.2 (using .../libhal1_0.5.7-1ubuntu19givre2_i386.deb) ...
Unpacking replacement libhal1 ...
Preparing to replace hal 0.5.7-1ubuntu18.2 (using .../hal_0.5.7-1ubuntu19givre2_i386.deb) ...
Unpacking replacement hal ...
Preparing to replace hal-device-manager 0.5.7-1ubuntu18.2 (using .../hal-device-manager_0.5.7-1ubuntu19givre2_all.deb) ...
Unpacking replacement hal-device-manager ...
Preparing to replace libhal-storage1 0.5.7-1ubuntu18.2 (using .../libhal-storage1_0.5.7-1ubuntu19givre2_i386.deb) ...
Unpacking replacement libhal-storage1 ...
Preparing to replace pmount 0.9.11-1ubuntu1 (using .../pmount_0.9.11-1ubuntu2givre8_i386.deb) ...
Unpacking replacement pmount ...
Setting up libhal1 (0.5.7-1ubuntu19givre2) ...

Setting up hal (0.5.7-1ubuntu19givre2) ...

Setting up hal-device-manager (0.5.7-1ubuntu19givre2) ...
Setting up libhal-storage1 (0.5.7-1ubuntu19givre2) ...

Setting up pmount (0.9.11-1ubuntu2givre8) ...

root@erich-desktop:~# sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@erich-desktop:~# sudo fdisk -l|grep NTFS
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS
root@erich-desktop:~# sudo gedit /etc/fstab
root@erich-desktop:~# gksu gedit /etc/modules
root@erich-desktop:~# sudo modprobe fuse
root@erich-desktop:~# sudo umount -a
umount: /dev: device is busy
umount: /var/run: device is busy
umount: /: device is busy
root@erich-desktop:~# sudo mount -a
root@erich-desktop:~#
```

When I double click the NTFS drive in Ubuntu 6.06 I get the following error:

```
error opening partition device: device or resource busy

failed to startup volume: device or resource busy

failed to mount '/dev/hda1': device or resource busy

mount is denied because the ntfs volume is already exclusively opened.

the volume may be already mounted, or another software may use it which

could be identified for example by the help of the 'fuser' command.
```

When I double click the NAT32 external USB hard drive in Ubuntu 6.06 I get the following error:

```
error: could not get sysfs directory

error: could not execute pmount
```

I can't believe it's this hard to mount two hard drives! :-?

---

### Post by XtremeSki2001 on 2007-01-11
I had to reinstall Ubunutu 6.06 because of NVIDIA issue.

That being said, now everything is back to default.

I'm looking for a guide or advice on mounting my exernal USB FAT32 drive AND my internal NTFS windows harddrive.

---

### Post by jd65pl on 2007-01-11
Try searching the forums, I already posted a link in this thread on how to mount your NTFS drive the wiki will also be useful for finding this information.

These questions have been asked and answered many times try looking for them instead of duplicating them.

---

### Post by XtremeSki2001 on 2007-01-11
> **jd65pl said:**
> Try searching the forums, I already posted a link in this thread on how to mount your NTFS drive the wiki will also be useful for finding this information.

These questions have been asked and answered many times try looking for them instead of duplicating them.

Thanks.  Oddly enough, after I did a fresh install ... what you recommended worked

---

### Post by Enverex on 2007-01-11
> **XtremeSki2001 said:**
> I had to reinstall Ubunutu 6.06 because of NVIDIA issue..

Eeek, that's excessive, you only ever really need to re-install if your base toolchain apps (bash/dash, etc) get hosed somehow and even then on a binary distro is easy to overwrite them, but I guess it's also not that hard to reinstall on a binary distro either due to the speed of install.

---

### Post by XtremeSki2001 on 2007-01-13
This is SO odd.

I did the above and my external USB FAT32 was mounted and ready to roll.

Now I just tried adding music from it to Banshee and halfway through the import the drive was unmounted ... I goto mount it and it tells me only root can do so ... I put in my password and viola, it's mounted again, only to disappear shortly.

WTF is the deal with this?  Is there a way that the drive can be mount on start-up?  Maybe this will stop it from unmount and remounting over and over.

---

