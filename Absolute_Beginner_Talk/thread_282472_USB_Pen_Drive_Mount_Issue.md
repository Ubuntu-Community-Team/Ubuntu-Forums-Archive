---
title: "USB Pen Drive Mount Issue"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by begeland on 2006-10-22
I'm running dapper on dell Inspiron 630m laptop.  Kernel 2.6-15-27-386

I'm having a problem with mounting any usb storage devices.  This includes a pen drive, portable drive as well as my digital camera (Olympus 5050Z). When I connect each of the devices, the system automatically starts "KDE Daemon" and shows the device as an "unmouted removable medium".  2 options are listed: 1) Do Nothing, 2) Open in new Window.  When I select open in new window, nothing happens. 

I cant find the drive in /media or /mnt directories.  However if I run

fdisk -l

It lists the devices as sdb, sdc, etc. - depending on what USB plug I use.

Can anyone help with this?  I want to mount these as removal media automatically when they're inserted.

---

### Post by ReaderRat on 2006-10-22
Run:
```
cat /etc/fstab
```
And post the results, please.

EDIT: I have found that if I plug in the pendrive before booting, it comes up on the desktop & mounted .

---

### Post by begeland on 2006-10-23
So I've got my swap/ubuntu installed on the second/third partitions.  First partition is for win2k and fourth is a fat32 partition for accessing files in both environments.  Interesting - if I run fstab I get the following: 
```

cat /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda4       /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda2       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```
No drive is listed here.  But if I run fdisk I get:

```
fdisk -l

Disk /dev/sdb: 512 MB, 512483328 bytes
16 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         992      499851+   6  FAT16

```

So sdb1 is the portable drive.  The prompt continues to appear asking me what I want to do when I put the USB drive in.  I always select I select "open in new window", but it never shows up.  In addition, the drive does not show up when I boot the computer up with the drive in place.

I did have this drive working in ubuntu, but not in kubuntu.  Any Ideas?

---

### Post by CujoQuarrel on 2006-10-23
For my USB mmc card reader there is never an entry in the fstab but it mounts and an entry appears in the mtab file. Ditto if I put in a USB pen drive.

Obviously something is monitoring the USB ports and automounting the drives. So I don't think not having entries in your fstab is the problem.

---

### Post by CujoQuarrel on 2006-10-23
Another thought.

Look at the file /proc/partitions before and after inserting the pen drive. My setup modifies this file automatically somehow.

---

### Post by NZ-Wanderer on 2006-12-01
I have exactly the same problem as you....

In Ubuntu the pen drive works perfectly, however in Kubuntu it doesn't..

If I goto system menu, storage media, and choose storage media in the left side, the pen drive shows up..

However, if I click on it I get: "Unknown error occured"
If I right click on it click on "mount" I get: "Unknown error occured"

In Ubuntu I didn't have to do anything, it was just there and worked perfectly, but in Kubuntu even tho it shows up, I can't do anything with it ](*,) ](*,) 

> **begeland said:**
> I did have this drive working in ubuntu, but not in kubuntu.  Any Ideas?

---

### Post by bodhi.zazen on 2006-12-01
Ubuntu (gnome) auto mounts with gnome-volume-manager which in turn uses pmount...

I am not sure about KDE or XFCE.

At any rate, in a terminal:```
pmount /dev/sdb1 sdb1
```

You should get a directory /media/sdb1 where the drive is mounted.

Post any error messages.....

To unmount:```
pumount /dev/sdb1
```

---

### Post by NZ-Wanderer on 2006-12-01
Thank you...

Yup, that worked perfectly. (although I used sda1 instead of sdb1)

I can now see my usb drive, read and write to it with no problems..

Now, my next question has to be:

Can I have this done automatically doen for me so I don't have to goto terminal all the time?? :D 

> **bodhi.zazen said:**
> At any rate, in a terminal:```
pmount /dev/sdb1 sdb1
```
You should get a directory /media/sdb1 where the drive is mounted.
Post any error messages.....
To unmount:```
pumount /dev/sdb1
```

---

### Post by eriefisher on 2006-12-01
The update last week seem to break something. I was told to put a line in my etc/fstab and it works for now but its just a workaroud.

mkdir /media/USBMEMORYSTICK

in fstab:

/dev/sdf1 /media/USBMEMORYSTICK vfat umask=0,uid=0,gid=0,noauto,rw,user 0 0

WORKS FOR ME

---

### Post by bodhi.zazen on 2006-12-01
> **NZ-Wanderer said:**
> Thank you...

Yup, that worked perfectly. (although I used sda1 instead of sdb1)

I can now see my usb drive, read and write to it with no problems..

Now, my next question has to be:

Can I have this done automatically doen for me so I don't have to goto terminal all the time?? :D

Apparently not (see the post above this).

You can make this easier if you give you USB drive a label and put an entry inf fstab something like this:> LABEL=<label> <mount_point> auto user,noauto 0 0

You can then mount with: mount LABEL=<label>

This is easier as the device mount point can vary....

[See here for details (how to FSTAB)](http://ubuntuforums.org/showthread.php?&t=283131)

---

