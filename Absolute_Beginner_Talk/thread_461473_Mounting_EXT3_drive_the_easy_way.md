---
title: "Mounting EXT3 drive the easy way?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Thorun on 2007-06-01
I decided to have a data drive to store my music and other stuff - so my "total system backup" will not include my data-stuff. 

In Partition Magic i made a ext3 extended partition on my 60gb drive.I now have read a lot of guides how to mount it. But it doesn't seem to work. 
I mounted my ntfs-data drive with Synaptic NTFS-something perfectly - and it did place an disk-icon on the desktop and in my "computer" allso as a disk-icon. 

Now my question is: Is there anyway as easy as mounting the NTFS-drive, to mount my ext3-drive?
If yes: How?
If no: I have tried several other guides with the Terminal and editing in the /etc/fstab document. Now it says, that my drive is mounted in my /storage folder. In this folder - by the way - there is now a new folder called "lost+found".
But... i can't seem to find the new "drive-icon" anywhere. And i don't know if it really is mounted or not?!
I used this guide - but wit no success:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

I failed at the command: sudo mount -a

it says:
FUSE mount point creation failed
Unmounting /dev/disk/by-uuid/32A01C98A01C651F (Lokal disk)


What i aiming for:
Mount my ext3-drive as a drive like the other drives that show up in the "computer" folder. 
Allso to have the shortcut to the drive on my desktop. 


Can someone please help??




with the sudo fdisk -l

  Device Boot      Start        End      Blocks  Id  System
/dev/hda1              1          10      80293+  de  Dell Utility
/dev/hda2  *          11        1431    11414182+  7  HPFS/NTFS
/dev/hda3            1432        2404    7815622+  83  Linux
/dev/hda4            2405        7296    39294990    f  W95 Ext'd (LBA)
/dev/hda5            2405        2599    1566306  82  Linux swap / Solaris
/dev/hda6            2600        3619    8193118+  83  Linux
/dev/hda7            3620        7296    29535471    7  HPFS/NTFS

---

### Post by taurus on 2007-06-01
You need to mount it to /media (like /media/storage) if you want to see an icon on your desktop for that partition.  So, edit /etc/fstab and replace /storage with /media/storage and create a new mount point for it as well.

```
sudo mkdir /media/storage
```
Then, reboot.

---

### Post by Thorun on 2007-06-01
Hehe. 
Placing the storage in the media-folder made my hopes come true. It made a desktop shortcut, and it now shows up as a separate harddisk drive when clicking on "computer" in the file browser. 

Thank you :D

/Rune
Denmark.

---

