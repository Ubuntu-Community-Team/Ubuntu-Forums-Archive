---
title: "Reformatting my Windows disk...help!"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by Irish J on 2006-10-16
So, I have 2 disks, hda = windows, hdd = dapper.

My XP install has become corrupt (surprise surprise!) and needs re-formatted.  Now, how do i go about this so as to stop my ubuntu install from failing. 

There are issues with windows over-writing Grub, etc.

My plan atm is to copy my documents, music etc over to my Linux drive, and then reformat my windows drive, reinstall XP and return to normal.

Any ideas?

---

### Post by grim918 on 2006-10-16
To copy your files to linux you should mount the windows drive onto your linux box. Then you can just copy all of the files onto the directory that you choose. 


To mount the windows partition use a command similar to this.
> sudo mount /dev/hda* /mnt/ntfs

To copy your files use this once the partition is mounted.
> sudo cp /mnt/ntfs/* /home/user/dir 
make sure to replace user with your user name and dir with the directory of your choice.

To format the partition you can use gparted and just format the windows partion into the filesystem that you want. Example: ext3

---

### Post by ReaderRat on 2006-10-16
> **Irish J said:**
> So, I have 2 disks, hda = windows, hdd = dapper.

My XP install has become corrupt (surprise surprise!) and needs re-formatted.  Now, how do i go about this so as to stop my ubuntu install from failing. 

There are issues with windows over-writing Grub, etc.

My plan atm is to copy my documents, music etc over to my Linux drive, and then reformat my windows drive, reinstall XP and return to normal.

Any ideas?
Try This:.....
ReInstalling Windows & Recovering Ubuntu
          [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

