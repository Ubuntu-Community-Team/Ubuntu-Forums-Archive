---
title: "Full install question"
date: 2005-09-28
forum: Absolute Beginner Talk
---

### Post by Dayylin on 2005-09-28
First off, howdy all. I've been playing around with the LiveCD and loving it. My question is, if I do a dual boot (XP and Ubuntu) will the Linux section see my FAT32 drives?  My wife needs XP (afraid to try something new) so I have keep some of it there til she gets her comp back from her mother who is using it.

Been reading and the support response here has been excellent.

Brian

---

### Post by wishyjr on 2005-09-28
as someone who has just setup a dual boot system with XP and Ubuntu (and is a bit new to all this), i can can tell that when you install, Ubuntu can see a FAT32 formatted partition, however you have to mount it for Ubuntu to see and use it.

when you get to the partitioning part of the install, it'll detect the partition with XP on and just leave it alone. but MAKE SURE YOU MANUALLY EDIT THE PARTITION TABLE!! dont let it do an automatic setup of the filesystem.

create an ext3 partition for Ubuntu, create a swap partition and if you want a 'drive' usable by both XP and Ubuntu create another FAT32 partition and mount it as something.

Hope that helps you mate!

---

### Post by arunsub on 2005-09-28
After you install Ubuntu do the following to mount the windows partition when Ubuntu loads.

How to mount Windows partitions (FAT) on boot-up, and allow all users to read/write?

   1. Read General Notes
   2. Read How to list partition tables?
   3.

      e.g. Assumed that /dev/hda1 is the location of Windows partition (FAT)
           Local mount folder: /media/windows

   4.

      sudo mkdir /media/windows
      sudo cp /etc/fstab /etc/fstab_backup
      sudo gedit /etc/fstab

   5. Append the following line at the end of file

      /dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

For more info: [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by Dayylin on 2005-09-28
Follow up question: Is it possible to install ubuntu to an existing system? As in, I already have XP loaded and would like to add ubuntu to it. Will that mess up the data already on the XP side of it?

Again, thanks for the fast responses.

---

### Post by arunsub on 2005-09-28
[QUOTE=Dayylin]Follow up question: Is it possible to install ubuntu to an existing system? As in, I already have XP loaded and would like to add ubuntu to it. Will that mess up the data already on the XP side of it?
Again, thanks for the fast responses.[/QUOTE]
You can. I did that twice. For safer side, take a back up of your data before doing that. Ubuntu installer can manually partition the disk to allocate space for Ubuntu installation. Go for manual parition and select the space you want to use as ext3 file system. I used partition magic and allocated space for Ubuntu from Windows itself and then formatted with Ubuntu installer.

---

### Post by az on 2005-09-28
[QUOTE=Dayylin]Follow up question: Is it possible to install ubuntu to an existing system? As in, I already have XP loaded and would like to add ubuntu to it. Will that mess up the data already on the XP side of it?
Again, thanks for the fast responses.[/QUOTE]

Breezy (wait three more weeks, or use it right away...) will make partitioniong easier.  The default will be that if there is already an OS there with sufficient free space on it, it will offer to shrink that partition for you.

Also, breezy includes an easier way to manage your other partitions.  You will be able to access them without having to edit your fstab by hand.

---

