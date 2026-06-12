---
title: "2nd day on ubuntu"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by The Healer on 2007-04-12
cant mount this drive ?
ive tried all ive seen here on the forum 



root@Rod:/home/rod# fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       13999   112446936   83  Linux
/dev/hda2           14000       14593     4771305    5  Extended
/dev/hda5           14000       14593     4771273+  82  Linux swap / Solaris

Disk /dev/hdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       30401   244196001   42  SFS
root@Rod:/home/rod#

---

### Post by Scunizi on 2007-04-12
I assume you mean the hdd1 drive (large).  I don't recognize the file system.  What is it?  If you haven't already check it out, take a look at [https://help.ubuntu.com/community/Mount?highlight=%28mount%29](https://help.ubuntu.com/community/Mount?highlight=%28mount%29).

---

### Post by The Healer on 2007-04-12
and this means ??

root@Rod:/home/rod# mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

---

### Post by The Healer on 2007-04-12
Disk /dev/hdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

this one yes 


and ive tryed that site no help or im doing something wrong

---

### Post by Scunizi on 2007-04-13
If you want to mount the drive at boot up so you won't have to mess with the mount command all the time, you'll need to do a couple of things.  

1> Determine the file system type ... from the terminal type fdisk -l (that last character is an L)
      It looks like you already did this ref. your 1st post.  hdd1 does not show a file system like your other drives do.

2> Format the drive to the file system you want to use.  If you're dual booting with Windows you may want to format it in vfat or fat32.  You also have the option of formatting it in EXT3 which is readable by windows with an add on driver. 

3> To format with ext3 (or anything else) the easiest way is to go to the synaptic package manager and search for gparted.  If it's already installed great otherwise install it.  Now go to your terminal and type "sudo gparted".  Gparted will start with a gui interface showing you info on the default drive.  In the upper right of the box change the drive to hdd.  It will now show you how the drive is currently partitioned or if it isn't partitioned.  If you are going to use this as a data drive you'll only need to make one partition. Highlight "unallocated" and right mouse click.  Choose "New".  If you want to format in ext3 then all the defaults should be fine.  Just verify that ext3 is the chosen file system type.  Now click apply and gparted will partition and format the drive.  If you're going to get fancier with the partitioning, remember that you can only have 4 primary partitions on a drive.  If you need more then make your 3rd partition an extended partition and you'll be able to add more below it.

4> Once it's formatted you can exit gparted but keep the terminal open.  You need to add a "folder/directory" referance for the drive.  In the terminal type "sudo mkdir /media/Data".  You can substitute Data for anything else you want.  If you have multiple partitions you'll need to repeat this giving a different name for each partitioin.  A pretty standard way of naming the partitions is with the correct term for the drive.. like... hdd1 (first partition, hdd2 (second partition) etc....  

5> Now you'll have to tell the system to mount the drive(s).  This is done by editing a file called fstab.  In the terminal type "sudo gedit /etc/fstab".. You are now in a text editor looking at the contents of fstab.  Assuming you formatted the partitions with ext3 you'll need to add a line in the file.

/dev/hdd1	/media/hdd1	ext3	rw,user	0	1

Now save the fstab file and reboot.  If you labeled the drive hdd1 it should show up that way on your desktop.

The hdd1 in the section reading /media/hdd1 is the lable you made in item 4 above.

Note:  I had an unformatted partition on one of my drives and attempted to mount it... I had issues getting it right in fstab but finally worked it out.  I got a lot of help from [http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm).  You may need to referance this if you are on edgy or fiesty.  I'm using Dapper.  With the release of edgy and fiesty they have started using UUID identifiers.  I haven't tinkered with that but it should be pretty close to what I've described with a couple of twists.  

Let me know how it goes.

Here's an entire list of my fstab for referance.  There's many things here..

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb3       /               reiserfs notail          0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb5       /media/sdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1	/media/hda1	vfat	user,auto,fmask=0111,dmask=0000
/dev/sda2	/media/sda2	ext3	rw,user	0	1


---

