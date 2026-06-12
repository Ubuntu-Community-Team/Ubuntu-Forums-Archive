---
title: "Mounting HDD problems"
date: 2005-11-01
forum: Absolute Beginner Talk
---

### Post by keeganisafish on 2005-11-01
So I have two NTFS partitions (hda7 and hdb1) and one FAT32 partition (hda1), not to mention the EXT3 for Ubuntu. Anyway, I looked up mounting hard drives and came accross [http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs) that said to use these commands

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

for NTFS and 

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

for FAT partitions.

I did this, but everytime I log out it un mounts them, so I have to do this everytime I start up! Is there anyway to have the hdds mounted permanently (until I decide/not to decide to umount them) or have something mount them as I start up? Plus, is there anyway to have the hard drives show up on the desktop like in Knoppix? Thanks for anything you can offer.

---

### Post by Kapre on 2005-11-01
[QUOTE=keeganisafish]So I have two NTFS partitions (hda7 and hdb1) and one FAT32 partition (hda1), not to mention the EXT3 for Ubuntu. Anyway, I looked up mounting hard drives and came accross [http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs) that said to use these commands

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

for NTFS and 

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

for FAT partitions.

I did this, but everytime I log out it un mounts them, so I have to do this everytime I start up! Is there anyway to have the hdds mounted permanently (until I decide/not to decide to umount them) or have something mount them as I start up? Plus, is there anyway to have the hard drives show up on the desktop like in Knoppix? Thanks for anything you can offer.[/QUOTE]


Seems like you did not finish the mounting guide till editing your fstab so that it would mount everytime you start your computer. Please see the guide again and finish it till the editing and mounting the drive everytime you start.

K

---

### Post by GreyFox503 on 2005-11-02
You're gonna die after realizing how close you are to it :)

Scroll down just a little bit on ubuntuguide.org (right below the part you linked to) It gives separate instructions for permanently mounting partitions (on startup).

---

