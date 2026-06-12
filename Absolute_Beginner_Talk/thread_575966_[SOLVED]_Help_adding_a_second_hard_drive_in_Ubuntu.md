---
title: "[SOLVED] Help adding a second hard drive in Ubuntu 7.04"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by vortex0007 on 2007-10-14
I have a second hard drive physically installed in the system. There is nothing on the drive that needs to be preserved. The current configuration looks like this:


Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4658    37415353+  83  Linux
/dev/sda2            4659        4863     1646662+   5  Extended
/dev/sda5            4659        4863     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

My brain feels like it has exploded from reading about how Linux works and I'm so lost at this point I'm pulling my hair out.

Can someone please give me the step-by-step details for what I need to do to to create 2 partitions on the 250GB drive and make them available to the system?

---

### Post by Shazaam on 2007-10-14
Download and burn the gparted livecd-
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Set your pc to boot to the cd, if you have problems geting it to display properly when it boots reboot the gparted livecd and choose "Force Vesa driver" and it will boot.
Since you already have a working main hard drive I would first make an EXTENDED partition to take up the whole 250gig drive. That way you won't hit the 4 primary partition limit. From there it's up to you how many and what type of partitions you want to add inside the extended partition. 
What do you plan to put in those partitions?

---

### Post by overdrank on 2007-10-14
> **vortex0007 said:**
> I have a second hard drive physically installed in the system. There is nothing on the drive that needs to be preserved. The current configuration looks like this:


Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4658    37415353+  83  Linux
/dev/sda2            4659        4863     1646662+   5  Extended
/dev/sda5            4659        4863     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

My brain feels like it has exploded from reading about how Linux works and I'm so lost at this point I'm pulling my hair out.

Can someone please give me the step-by-step details for what I need to do to to create 2 partitions on the 250GB drive and make them available to the system?

HI if you have the live cd you can boot it and then use gparted to partition the drive. Under system, administration, gparted on the live cd it will allow you to delete, create, resize partition as  you like. Hope this helps good luck! :KS

---

### Post by Frak on 2007-10-14
1) In the top right hand corner, choose /dev/hdb

2) Right-click on the white bar and choose "New."

3) For "New Size" the number should be the maximum allowable, to fill the entire disk.

4) Choose "Primary Partition"

5) Now decide on a filesystem. Use "ext3" if the drive will only be used with Ubuntu. For file-sharing between Ubuntu and Windows, you should use "fat32."

6) Now click Add to create the partition. The display should update to show a new partition covering the entire disk.

7) To finish, click "Apply," or Edit > Apply. The disk will then be partitioned and formatted.

Now, in the terminal run

```
sudo tune2fs -m 0 /dev/sdb1
```
```
sudo tune2fs -m 0 /dev/sdb2
```

This will make Ubuntu free up any emergency reserves on the disk (this is only needed on the main drive)

Make a new mount point
```
sudo mkdir /media/sdb
sudo mkdir /media/sdb2
sudo mount /dev/sdb1 /media/sdb1
sudo mount /dev/sdb2 /media/sdb2
```

Now to make it mount at boot
```
gksudo gedit /etc/fstab

```
add this to the end of it
```
/dev/sdb1    /media/sdb1   ext3    defaults     0        2
/dev/sdb2    /media/sdb2   ext3    defaults     0        2
```

Then change ownership to you
```
sudo chgrp plugdev /media/sdb1
sudo chmod g+w /media/sdb1
sudo chmod +t /media/sdb1
sudo chgrp plugdev /media/sdb2
sudo chmod g+w /media/sdb2
sudo chmod +t /media/sdb2
```

You can now run "sudo mount -a" (or reboot the computer) to have the changes take effect.

Thats all it takes :)

---

### Post by vortex0007 on 2007-10-14
I downloaded gparted-livecd-0.3.4-8.iso, booted from it, used it to create my partitions. It created them successfully and when I boot back into Ubuntu, they show up under Places > Computer - but I have discovered that they were created with the permissions to only allow owner: root to use the files.

The Disk properties for both new partitions look like this:

Owner: root
Folder Access: Create and delete files
Group: root
Folder Access: Access files
Others
Folder Access: Access files

How can I reset these so that my standard user account can use the drives?

The other problem is that when they are accessed using Computer - File Browser, they show up as follows:  

CD-ROM 1
163.9 GB Volume: disk
68.9 GB Volume: disk-1
Filesystem

can the volume names be changed?

---

### Post by Frak on 2007-10-14
Gparted is already installed in Ubuntu, you need to use that, not the CD version.

The CD version will just give it to root for security.

---

### Post by vortex0007 on 2007-10-14
do should I delete the new partitions and start over?

---

### Post by Frak on 2007-10-14
> **vortex0007 said:**
> do should I delete the new partitions and start over?
Just follow my guide above and it should work just fine.

---

### Post by vortex0007 on 2007-10-14
Thanks to everyone for the quick replies and the help. I started over using the built in GPARTED tool and after a couple of reboots was able to make this work.

---

