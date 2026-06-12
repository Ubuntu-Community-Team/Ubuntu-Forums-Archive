---
title: "Help with fstab"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Shazaam on 2007-04-15
To make a long story short I have completely trashed fstab in Ubuntu by deleting and resizing partitions AND by manually editing fstab to the point that I can't boot Ubuntu or Mepis anymore.  What I humbly ask is if someone could post how fstab should look with the partitions that I have now. Googling fstab has taught me that I should NEVER have manually changed fstab without a backup plan.

The partitions that are on hd0...
hda1= extended partition
hda5=swap
hda6=Mepis
hda7=Ubuntu
No shared /home folder

I have Ubuntu Dapper 6.06 Desktop and since I am on dialup downloading 700mb to get the alternate Ubuntu cd to repair the installation  is out of the question. I can boot the drive with the livecd and I can mount and unmount partitions fine. I know I could just as easily reinstall Ubuntu but  it would be nice to get back to a working system again. Reinstalling Mepis after getting  Ubuntu working again isn't a problem.
Any help would be appreciated.

---

### Post by confused57 on 2007-04-15
You might want to boot the live cd & post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

Also, you might want to mount your Ubuntu root partition and post your current /etc/fstab:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

### Post by Shazaam on 2007-04-15
confused57...
Yes I can do that. Will post back shortly.

---

### Post by louieb on 2007-04-15
Just by way of example here is my Dapper fstab. sda1 is windows, sda2 is Dappers / (root). sda3 is swap, sda6 is Dappers home.  sda5 and sda8 contains a Ubuntu Feisty install, and sda7 is a PCLinuxOS install.  Maybe you  can work with this and see where you fstab is messed up.  

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /home           ext3    defaults        0       2
/dev/sda5       /media/sda5     ext3    defaults        0       2
/dev/sda7       /media/sda7     ext3    defaults        0       2
/dev/sda8       /media/sda8     ext3    defaults        0       2
/dev/sda1       /media/winxp    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
Be glad you have Dapper and don't have to mess with UUID's.

---

### Post by Shazaam on 2007-04-15
confused57...
fdisk-

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25683   206298666    7  HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        9729    78148161    5  Extended
/dev/hda5               1        1572    12627027   82  Linux swap / Solaris
/dev/hda6            1573        4296    21880498+  83  Linux (Mepis)
/dev/hda7            4297        9729    43640541   83  Linux (Ubuntu)
ubuntu@ubuntu:~$


Ubuntu fstab-

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /media/hda6     ext3    defaults        0       2
/dev/hda7       /media/hda7     ext3    defaults        0       2
/dev/hda8       /media/hda8     ext3    defaults        0       2
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0



/dev/hda8 is a remnant, probably needs to be commented out. One thing I just noticed is its trying to mount hda7 as / and again as /media/hda7.

---

### Post by confused57 on 2007-04-15
Shazaam,  comparing your fstab with louieb's(thanks for posting), your entries look OK...you can try commenting both the /dev/hda8 & the duplicate /dev/hda7.

If this doesn't work, you might want to use the live cd & post the output of your /boot/grub/menu.lst.

---

### Post by Shazaam on 2007-04-15
confused57..

Thank you, I will try that and post back as soon as I can.

---

### Post by Shazaam on 2007-04-16
Thank you for all of the help. I kept fooling with it but couldn't fix the problem. So, I wiped the drive and started over WITH a backup plan and I have decided to RTFM before wandering under the hood again.

One good thing that has happened is I was able to get Mandriva One to play nice with Mepis and Ubuntu. If anyone is having trouble multi-booting with Mandriva here is a hint--- Mandriva One adds a HIDDEN partition that Ubuntu's LiveCD  ignores. What happened to me before is after having installed  Mandriva One, gparted on the Ubuntu live cd shows a BLANK (unformated) drive. Crazy. The Mepis live cd was able to show me what was going on. Un-hid the Mandriva One partition and the other installs went fine. :)

---

### Post by confused57 on 2007-04-16
> **Shazaam said:**
> Thank you for all of the help. I kept fooling with it but couldn't fix the problem. So, I wiped the drive and started over WITH a backup plan and I have decided to RTFM before wandering under the hood again.

One good thing that has happened is I was able to get Mandriva One to play nice with Mepis and Ubuntu. If anyone is having trouble multi-booting with Mandriva here is a hint--- Mandriva One adds a HIDDEN partition that Ubuntu's LiveCD  ignores. What happened to me before is after having installed  Mandriva One, gparted on the Ubuntu live cd shows a BLANK (unformated) drive. Crazy. The Mepis live cd was able to show me what was going on. Un-hid the Mandriva One partition and the other installs went fine. :)

Glad you were able to work things out...excellent info concerning Mandriva One's hidden partition(s).

---

