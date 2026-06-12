---
title: "[SOLVED] help mounting ntfs partition with my music on it"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by DarinB on 2007-08-26
i need some expert advise.
i have an internal extra drive ntfs with all my music on it from my about 55 Gigs of music.
i run a 160 Gb ubuntu only machine and want the partition to mount at boot.
so i don't have to do it manually each time.
i tried ntfs-3g and the config setup it still is visible but i have to click it from my home folder and enter my root password.

i tried the diskmounter script but it kill my machine i didn't unmount the ntfs before running it or delete any fstab lines with ntfs before.

so i reinstalled my whole system and here i am again at the same point.

SHOULD I????
Ideas: change ownership of the drive via
sudo chown usr:usr /media/disk-1/
OR
should i manually edit fstab? and try it 
OR
 delete the ntfs lines in fsatb unmount remove ntfs-3g and ntfs config run the diskmounter again or will it be suicide again 
OR 
delete all and try ntfs-3g again which has never worked on my last three tries on two different machines.
OR
any other ideas, 
i did find how to automatically mount drive on the forums with an explanation of the paths and usr id and stuff. to do it manually.

what do the experts think??
I need some clear direction because this has caused me some big mess ups already and i am not really up to going through another total reinstall.

i think i will give up on ubuntu if i do.
thank db

---

### Post by logos34 on 2007-08-26
try this guide:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

post back if you have any questions

---

### Post by DarinB on 2007-08-27
it shows up in my hole folder places but unmount when i click to mount it asks for root root password the it mounts and is read write able.



Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19175   154023156   83  Linux
/dev/sda2           19176       19457     2265165    5  Extended
/dev/sda5           19176       19457     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9091    73023426    7  HPFS/NTFS
/dev/sdb2            9092        9729     5124735   83  Linux

---

### Post by DarinB on 2007-08-27
OK i did tha above i created a mount point I called it sudo mkdir /mnt/itunes
i backed up fstab
i edited it with gedit to 
/dev/sdb1 /media/itunes ntfs nls=utf8,umask=0222 0 0

then it didn't mount at boot and came up no permission to mount this volume when i went to mount it manually by clicking it

so i restored the back up and now what???

---

### Post by vanadium on 2007-08-27
I am not sure how ntfs-3g works when used from fstab because I use it only on a removable drive. I know, however, that in fstab, you need to specify the system to use the ntfs-3g driver in order to have read/write access. Currently, you are instructing Linux to use the default (read only) ntfs driver. Therefore, first change ntfs in your fstab line to ntfs-3g. Also change the permissions of your mount point, /media/itunes to 777 (read, write and execute permissions for anybody). Instead of restarting the system, you can do "sudo mount -a" for the system to reread and remount the drives in fstab.

Since you are Ubuntu-only, reformatting the partition to ext3 would in fact be a better option. The reason I didn't is that my external drive is a Lacie silverscreen that has autonomous playback capabilities (need ntfs for playback of DVD ISO images).

---

### Post by logos34 on 2007-08-27
Is the mount point '/media/itunes' or '/mnt/itunes'?  

Given this is an ubuntu-only machine, I'd do as Vanadium suggested and format the drive ext3--IF, that is, you have 55 gigs of space on the 160GB drive or some other hard disk you can backup to (it will take a while to copy and restore).   

Otherwise I'd try ntfs-config again to enable write support--it will change that ntfs entry in fstab for you.  It's better than manually editing IMO--you're assured the entries are correct and properly configured so the ntfs-3g 'fuse' module can mount them with write support and user access.

So get the mount point right, and then try the ntfs-config gui again.  Check fstab to verify changes.  Then,

sudo mount -a

or reboot (which is sometimes necessary to get ntfs-3g to work correctly)

---

