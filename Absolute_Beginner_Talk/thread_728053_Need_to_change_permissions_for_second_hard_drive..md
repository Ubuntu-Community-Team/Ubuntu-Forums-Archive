---
title: "Need to change permissions for second hard drive."
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by pastoraaron on 2008-03-18
I just installed a second hard drive on my Gutsy system.  It is formatted ext3.  It will mount just fine but I cannot read or write to the drive.  I intend to use it for storage.  I tried using the permissions dialog under properties, but it will not take the change.  I am completely new to Ubuntu or anything Linux for that matter.  Any help would be appreciated.

---

### Post by sisco311 on 2008-03-18
open a terminal:

Applications -> Accessories -> Terminal

To change the owner of the partition type:
```
sudo chown -R *username:username* /media/*mountpointofthedrive*
```

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Diabolis on 2008-03-18
give a look to **chmod** and **chown** commands. By typing **_man chmod_** and **_man chown_**. I know they are hard to read, so google them too.
More info: 
[http://en.wikibooks.org/wiki/Guide_to_UNIX/Commands/File_System_Utilities#chown](http://en.wikibooks.org/wiki/Guide_to_UNIX/Commands/File_System_Utilities#chown)
[http://badcomputer.org/unix/permissions.bot](http://badcomputer.org/unix/permissions.bot)

You can also modify the properties of your partition in your partition table, you can look at it here:
```
sudo gedit /etc/fstab
```

give a look to the man page, **_man mount_**

I know the title says "how to mount windows partitions", but it still has some pretty good information about which options you can use on your partitions.
[http://gentoo-wiki.com/HOWTO_Mount_Windows_partitions_%28DOS%2C_FAT%2C_NTFS%29](http://gentoo-wiki.com/HOWTO_Mount_Windows_partitions_%28DOS%2C_FAT%2C_NTFS%29)

---

### Post by pastoraaron on 2008-03-18
> **sisco311 said:**
> open a terminal:

Applications -> Accessories -> Terminal

To change the owner of the partition type:
```
sudo chown -R *username:username* /media/*mountpointofthedrive*
```

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
sisco311, when you say /media/mountpointofthedrive are you talking about its name and location like /hdd1 /media? Sorry...like I said...I'm new.

---

### Post by Diabolis on 2008-03-18
The mount point is the folder in which you partition shows up. If you don't set one manually you'll see folders on your desktop named like this: disk, disk-1 etc.
 
I think is better to make your own mount points, this means create folders designated to hold your partitions. You can create them with this command:
```
sudo mkdir /media/NAME
```

The name can be whatever you want. So the route **/media/NAME** would become your mount point.

After that you only have to update fstab, if you post the contents of your fstab file I'll help you with that.

---

### Post by Diabolis on 2008-03-18
I forgot to mention it. You can use the mount points that you already have.
```
sudo chown -R username:username /media/disk
or
sudo chown -R username:username /media/disk-1
```

---

### Post by sisco311 on 2008-03-18
Don't forget to replace *username* from the commands with your user name(pastoraaron???).

If your unsure about the mount point, post the output of the commands:
```
mount
``````
sudo fdisk -l
``````
cat /etc/fstab
```

---

### Post by pastoraaron on 2008-03-18
> **sisco311 said:**
> Don't forget to replace *username* from the commands with your user name(pastoraaron???).

If your unsure about the mount point, post the output of the commands:
```
mount
``````
sudo fdisk -l
``````
cat /etc/fstab
```
Typing mount gets:
chadwick@chadwick-desktop:~$ mount
/dev/hdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/hdd1 on /media/disk type ext3 (rw,nosuid,nodev)

Typing sudo fdisk -l gets:
Disk /dev/hdc: 61.4 GB, 61475807232 bytes
255 heads, 63 sectors/track, 7474 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff471ce5

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        7286    58524763+  83  Linux
/dev/hdc2            7287        7474     1510110    5  Extended
/dev/hdc5            7287        7474     1510078+  82  Linux swap / Solaris

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe77ae77a

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       19457   156288321    7  HPFS/NTFS

Typing cat /etc/fstab gets:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=8a7037b4-5afe-41da-a11e-72ef5b513edf /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=89cfb741-b378-4699-9598-27ee9f6d11f1 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

I sincerely appreciate the help.

---

### Post by garyed on 2008-03-18
I'm just a novice but it looks like your 2nd drive has been formatted with Windows NTFS &
mounted as Ext3.  I don't have the answer but maybe you can unmount it & remount it using NTFS.

---

### Post by sisco311 on 2008-03-18
0.) format the partition with gparted to ext3
```
gksu gparted
```if gparted is not installed install it:
```
sudo aptitude install gparted
```1.) create a mount point:
```
sudo mkdir /media/hdd1
```2.) get the uuid of the partition:
```
blkid /dev/hdd1
```3.) edit fstab:
```
gksu gedit /etc/fstab
```add this line at the end of the file:

> 
#/dev/hdd1
UUID=**xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx** /media/hdd1    defaults        0       2replace **xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx** with the uuid you get from 2.)

4.) mount the partition:
```
sudo mount -a
```5.) change the owner of the partition to get write permission:
```
sudo chown -R **your_username:your_username** /media/hdd1
```done

---

### Post by sisco311 on 2008-03-18
> **garyed said:**
> I'm just a novice but it looks like your 2nd drive has been formatted with Windows NTFS &
mounted as Ext3.  I don't have the answer but maybe you can unmount it & remount it using NTFS.

Yes you 're right. 
I don't see any reason to use an ntfs partition on a single boot ubuntu system.

---

### Post by natirips on 2008-03-18
Try simply (using the console)```
sudo nautilus
```Now go to /media and right-click your drive, make yourself the owner of the drive and give yourself permissions to read/write. You can also click the "Apply permissions to enclosed files" button, (That is the procedure I used to get my "storage" partition work.

---

### Post by pastoraaron on 2008-03-18
I did everything you suggested.  Now I can't find hdd1.  Where would I find it?  Before, I could see the drive when I went to places-computer.  Any suggestions?

---

### Post by pastoraaron on 2008-03-18
> **sisco311 said:**
> 0.) format the partition with gparted to ext3
```
gksu gparted
```if gparted is not installed install it:
```
sudo aptitude install gparted
```1.) create a mount point:
```
sudo mkdir /media/hdd1
```2.) get the uuid of the partition:
```
blkid /dev/hdd1
```3.) edit fstab:
```
gksu gedit /etc/fstab
```add this line at the end of the file:

replace **xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx** with the uuid you get from 2.)

4.) mount the partition:
```
sudo mount -a
```5.) change the owner of the partition to get write permission:
```
sudo chown -R **your_username:your_username** /media/hdd1
```done
Sorry, I should have posted the info.

cat /etc/fstab gets:
chadwick@chadwick-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=8a7037b4-5afe-41da-a11e-72ef5b513edf /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=89cfb741-b378-4699-9598-27ee9f6d11f1 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
#/dev/hdd1
UUID=27cac049-425b-4e16-b389-ad9d0c2bc16e /media/hdd1 defaults 0 2

sudo mount -a gets:
chadwick@chadwick-desktop:~$ sudo mount -a
mount: unknown filesystem type 'defaults'

sudo chown -R chadwick:chadwick /media/hdd1 gets:
chadwick@chadwick-desktop:~$ sudo chown -R chadwick:chadwick /media/hdd1
chadwick@chadwick-desktop:~$ 

When I go to places-computer I can no longer find the drive hdd1.

---

### Post by pastoraaron on 2008-03-18
I can find hdd1 in the media folder, but it's as if it's a part of the filesystem (which I am assuming is hdc1, the first drive)  I used to be able to see my 160 gig drive in places-computer, but no longer.  I guess I really messed it up.  I can see the drive with linHDD but it shows not mounted.  Man, I'm really confused.

---

### Post by pastoraaron on 2008-03-18
Problem solved.  Thanks to all of you guys.

---

