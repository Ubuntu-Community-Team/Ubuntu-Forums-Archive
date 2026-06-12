---
title: "GRUB error 2 - need easy repair instructions"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by jbarrington on 2006-07-20
I’m a long time user of windows, but VERY recent user to Linux and to Ubuntu. Although I consider myself a “College Graduate” with DOS and Windows, I consider myself in the first weeks of “Kindergarten” with Ubuntu/Linux, so I’m still trying to connect the dots with this similar desktop environment but different DOS environment. Having said all that… 

I have installed Ubuntu as the only OS onto a computer with a 40gb drive that is connected to my home network. I have also updated the software whenever it has asked. 

I been casually playing with Ubuntu for around 1 1/2 to 2 months now, but I keep encountering only one persistent problem that has kept occurring once every week or every two weeks.

I get this error message:
========================
GRUB Loading stage1.5.

GRUB loading, please wait...

Error 2
========================
then it doesn’t do anything afterward, and then I end up having to reinstall Ubuntu and all of it’s updates again.

I think that I’ve had this problem occur me roughly about three times now, and I’m lost as to what causes it or how I can easily recover from it. Although I really like the OS, I don’t think that I like having to constantly re-install the system to correct this problem, but I feel there could be an easy way to correct it (or prevent it from happening) other than performing a semi-weekly re-installation. 

I’ve done a search on the internet, but most of the information only provides a definition of the error and the other information appears to deal with dual booting.

One thing that I did read was that people sometimes like to see the information from “sudo fdisk –l”

Disk /dev/hda: 40.0 GB, 40037760000 bytes
255 heads, 63 sectors/track, 4867 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4666    37479613+  83  Linux
/dev/hda2            4667        4867     1614532+   5  Extended
/dev/hda5            4667        4867     1614501   82  Linux swap / Solaris

Disk /dev/sda: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         992      999813+   6  FAT16


I’m not sure what other information I should include, but I would be glad to if asked. :)

---

### Post by Klemik on 2006-07-20
Did you get any errors while installing updates? Maybe you ran out of space so new linux image could be written to the disk. Also post your /etc/fstab file.

---

### Post by mcduck on 2006-07-20
Are you using some USB drive or something like that? Because if I have my CompactFlash memory attached when I boot it becomes sda changing my boot disk to sdb, and that results in the same error you have..

---

### Post by jbarrington on 2006-07-20
> Did you get any errors while installing updates? 
I'm assuming that any installation updates errors that may occur will be very obvious. I don't believe so, except perhaps possibly this last time (Last night). 

When it tried to update and install a large 21mb file. It was having a difficult time and I had to restart the same update several times until I noticed a large storm was hitting my area. After the storm passed where I lost power to my home, I tried to reboot and then that was when I got the GRUB error. That was the only time that I can recall getting an error. I may have gotten errors before, but never noticed them.

> Maybe you ran out of space so new linux image could be written to the disk. 
I'm really not sure how to tell if it doesn't have enough space. I wouldn't think that I've run out of space since I have a 40gb drive for the system to play in. :) 

> Also post your /etc/fstab file.
I've already re-installed the system again, but here it is. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0



> Are you using some USB drive or something like that? 
I do have a thumb drive that I used for the first time yesterday. I did use a USB floppy drive only once about a week ago. Each time I thought I was ejecting it properly. (Right clicking onto the device icon, and selecting EJECT.) When I select eject for the thumb drive, the LED light does stay on unlike when being ejected from within WXP.

> Because if I have my CompactFlash memory attached when I boot it becomes sda changing my boot disk to sdb, and that results in the same error you have..
I haven't had the thumb drive plugged in during any of past the boot processes

---

### Post by jbarrington on 2006-07-21
Bumping up for second breath of air.:)

---

