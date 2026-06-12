---
title: "hdd permissions"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by question_chick on 2007-05-27
Hi

I have 2 fat32 hard drives that I am trying to auto mount on startup. I have managed to get them to mount fine but when I try to change any files or directories I get told I don't have the permissions.

I have tried to chown them to my user but get the error that the operation is not permitted (yes I am using sudo)

There are also random locked directories in the hdds (the base data got transfered from another drive) and it wont let me unlock or change the permissions or ownership of those either.

I can rm files and dirs with sudo but I would like to be able to change the permissions of those hdds and the stuff within them to my ownership.

This is what my fstab looks like, could it be something in here?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/PsykezUbuntu-root /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc1
UUID=9395d3fa-90c8-4bd6-8452-7d65e150464e /boot           ext3    defaults        0       2
/dev/mapper/PsykezUbuntu-swap_1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


/dev/sdb5 /media/Music vfat iocharset=utf8,umask=000 0 0

/dev/sda5 /media/Other vfat iocharset=utf8,umask=000 0 0

---

### Post by taurus on 2007-05-27
What are the outputs of these two commands from a terminal?

```
sudo fdisk -l
ls -la /media
```

---

### Post by question_chick on 2007-05-27
psyke@PsykezUbuntu:~$ sudo fdisk -l
Password:

Disk /dev/sda: 122.9 GB, 122942324736 bytes
240 heads, 63 sectors/track, 15881 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         534     4037008+  1b  Hidden W95 FAT32
/dev/sda2   *         535        5952    40960080    7  HPFS/NTFS
/dev/sda3            5953       15881    75063240    f  W95 Ext'd (LBA)
/dev/sda5            5953       15881    75063208+   b  W95 FAT32

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        9729    78140160    f  W95 Ext'd (LBA)
/dev/sdb5               2        9729    78140128+   b  W95 FAT32

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          31      248976   83  Linux
/dev/sdc2              32        9729    77899185    5  Extended
/dev/sdc5              32        9729    77899153+  8e  Linux LVM



***************************************************************************************************

psyke@PsykezUbuntu:~$ ls -la /media
total 84
drwxr-xr-x  7 root root  4096 2007-05-27 16:32 .
drwxr-xr-x 21 root root  4096 2007-04-29 07:13 ..
lrwxrwxrwx  1 root root     6 2007-04-29 06:59 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2007-04-29 06:59 cdrom0
-rw-r--r--  1 root root     0 2007-05-27 16:32 .hal-mtab
--wsr-x---  1 root root     0 2007-04-28 19:27 .hal-mtab-lock
drwxr-xr-x  2 root root  4096 2007-04-29 13:11 More_Stuff
drwxrwxrwx  7 root root 32768 2007-05-27 15:22 Music
drwxrwxrwx  8 root root 32768 2007-05-27 15:22 Other
drwxr-xr-x  2 root root  4096 2007-04-29 13:10 Stuff


Is that all you needed?

---

### Post by taurus on 2007-05-27
What happens when you run

```
cd /media/Other
ls -la
```

---

### Post by question_chick on 2007-05-27
psyke@PsykezUbuntu:~$ cd /media/Other
psyke@PsykezUbuntu:/media/Other$ ls -la
total 11716
drwxrwxrwx  8 root root    32768 2007-05-27 15:22 .
drwxr-xr-x  7 root root     4096 2007-05-27 16:32 ..
drwxrwxrwx  2 root root    32768 2007-05-27 15:16 Movies
drwxrwxrwx 66 root root    32768 2007-05-27 15:04 My Pictures
-rwxrwxrwx  1 root root 11746722 2007-05-27 15:22 OfficialUbuntuBook.chm
drwxrwxrwx 23 root root    32768 2007-05-27 14:56 Photos
drwxrwxrwx  2 root root    32768 2007-05-27 14:56 Pics
drwxrwxrwx  4 root root    32768 2007-05-27 15:21 Stuff From WinBox
drwxrwxrwx  3 root root    32768 2007-05-27 15:22 Work

---

### Post by taurus on 2007-05-27
```
cd Photos
ls -la
```
And if you get a list of your photos, then you have successfully changed directory without problems (permissions).

---

### Post by question_chick on 2007-05-27
I can get into that drectory but that doesn't so much help with the random locked directories that I cant change ownership of or permissions to.

here is one of those directories

psyke@PsykezUbuntu:/media/Music/Music/Creed$ ls -la
total 224
dr-xr-xr-x   5 root root 32768 2007-02-04 18:27 .
drwxrwxrwx 126 root root 32768 2007-05-27 16:24 ..
-rwxrwxrwx   1 root root   274 2005-03-20 12:29 desktop.ini
dr-xr-xr-x   2 root root 32768 2007-02-04 18:28 Greatest Hits
dr-xr-xr-x   2 root root 32768 2007-02-04 18:27 Human Clay [Australia Bonus CD] Disc 1
dr-xr-xr-x   2 root root 32768 2007-02-04 18:27 My Own Prison [UK]
-rwxrwxrwx   1 root root 10752 2005-03-20 13:17 Thumbs.db

it wont let me change the permissions or ownership, can't even use sudo chown

---

### Post by taurus on 2007-05-27
The command chown won't work for ntfs/vfat filesystem.  Try

```
gksudo nautilus
```
and navigate to those directories on /media/Other then.

---

### Post by question_chick on 2007-05-27
Thanks, that has helped somewhat.

It still wont let me change the owner from root but it will let me change the permissions so that all others can read and write to files in that directory.

I would still like to be able to change to ownership of the folder to my current user if that's possible, or do I have to re format the partition to ex3 to be able to do that properly?

---

### Post by taurus on 2007-05-27
If you have an option, always use ext3 filesystem since it's much better and just so you know, you can read and write to ext3 partitions from XP with [http://www.fs-driver.org](http://www.fs-driver.org).

---

### Post by question_chick on 2007-05-27
So I take that to mean I can't change the directory ownership to psyke (me) without reformating in ex3?

Oh well, job for another day then, Thanks heaps for your help, at least the files are usable now.

Cheers

---

