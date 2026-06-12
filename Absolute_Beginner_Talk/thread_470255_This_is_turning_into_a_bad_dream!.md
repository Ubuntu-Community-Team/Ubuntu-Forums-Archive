---
title: "This is turning into a bad dream!"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by vacguy on 2007-06-10
I first installed Ubuntu 6.06 a few days ago.  I have several gigabytes of files backed up to a USB drive.  When I first installed 6.06 on my computer the USB disk with all my files would auto mount.  Then, mysteriously, it stopped mounting.  I tried several things on 6.06 before starting over and installed 7.04.  I still could not access the disk.  I could not mount the disk and it would not auto mount.  Then I tried the latest version of Knoppix.  It was able to mount all 5 partitions on my computer but it could not mount the USB disk.  I have several years of family pictures on this drive.  

I am totally freaking out!
I hope someone can help.

Here was my previous post.

[http://ubuntuforums.org/showthread.php?t=468067&highlight=vacguy](http://ubuntuforums.org/showthread.php?t=468067&highlight=vacguy)

---

### Post by Rocket2DMn on 2007-06-10
Have you set it to mount in /etc/fstab  ?
I suggest that you don't, if you have.
Also, plug in the drive and run the command 
```
sudo fdisk -l
```
and post the output

---

### Post by Tomosaur on 2007-06-10
If you've tried it on different systems, then I would expect that either your pen drive has conked out, or your usb port has conked out.

---

### Post by vacguy on 2007-06-10
I will try that command.

---

### Post by Rocket2DMn on 2007-06-10
> **vacguy said:**
> What does 

sudo fdisk -l

do for me?

Sorry for the delay.  When you run that in terminal, it will output data about the partitions that are connected to the computer.  With your USB drive plugged in we should be able to see it at the bottom, even if it isn't mounted yet.

---

### Post by vacguy on 2007-06-10
Here is what I got for sudo fdisk -ls.



caleb@vortex:~$ sudo fdisk -ls
Password:

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         124      995998+  82  Linux swap / Solaris
/dev/hda2             125         746     4996215   83  Linux
/dev/hda3             747       14946   114061500   83  Linux

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       12449    99996561   83  Linux
/dev/hdb2           12450       30401   144199440   83  Linux

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table


I think sda is for my USB disk.  Am I screwed?

---

### Post by Rocket2DMn on 2007-06-10
There is also an entry for /dev/hdb for 250 GB
If this might be your drive, try this:
```
sudo mkdir /media/usbdisk1
sudo mount /dev/hdb /media/usbdisk1
```
Then see if you can cd to there either normally or using sudo.  A good old "ls" should show you what's in the drive if any of this works.

---

### Post by Mimsy on 2007-06-10
I had a similar problem at one point, and this was the solution that worked for me. Worth trying?

[http://ubuntuforums.org/showthread.php?t=304420](http://ubuntuforums.org/showthread.php?t=304420)

---

### Post by vacguy on 2007-06-10
The other 250 gigabytes is in the computer.  I have 120 GB, 250 GB, and a 250 GB backup.  All are working except for the backup.

---

### Post by vacguy on 2007-06-10
> **Mimsy said:**
> I had a similar problem at one point, and this was the solution that worked for me. Worth trying?

[http://ubuntuforums.org/showthread.php?t=304420](http://ubuntuforums.org/showthread.php?t=304420)

1.  Was posted above on this page.




2.


caleb@vortex:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=aabb90ee-1147-4625-ad23-7f5f93d8aef9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=5ca85868-eb91-486d-8f19-ed026782e7c4 /extra          ext3    defaults        0       2
# /dev/hdb2
UUID=ebc1c58b-4e2e-4943-888a-cfc6f8fa3172 /extra2         ext3    defaults        0       2
# /dev/hda3
UUID=1fd0388d-bf49-4160-9047-a3fe441a14ce /home           ext3    defaults        0       2
# /dev/hda1
UUID=175cf6d7-4773-4ffd-b99b-21f25aa10698 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0




3.




caleb@vortex:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             4.7G  2.3G  2.3G  50% /
varrun                252M  104K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M  140K  252M   1% /proc/bus/usb
udev                  252M  140K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   33M  219M  14% /lib/modules/2.6.20-16-generic/volatile
/dev/hdb1              94G  188M   89G   1% /extra
/dev/hdb2             136G  188M  129G   1% /extra2
/dev/hda3             108G  215M  102G   1% /home
/dev/hdc              697M  697M     0 100% /media/cdrom0

---

### Post by vacguy on 2007-06-10
I am most concerned with this output line.

Disk /dev/sda doesn't contain a valid partition table

How can I fix this?

---

