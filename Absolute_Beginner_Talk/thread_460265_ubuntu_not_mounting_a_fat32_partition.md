---
title: "ubuntu not mounting a fat32 partition"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by buzzohall on 2007-05-31
i have got all my previous problems fixed however i have several partitions and ubuntu will not mount the fat32 partition. i thought that ubuntu was suposed to be able to recognize and mount fat32? am i doing somthing wrong?

---

### Post by Kobalt on 2007-05-31
Don't you see it in Places > Desktop ? You should be able to mount it from there with a double-click.

---

### Post by ajgreeny on 2007-05-31
Is the partition entered in your /etc/fstab file and if so how is it shown in the file?

As a double check of the filesystem try mounting it manually with the commands:-
sudo mkdir /media/fat32/  (this will make a folder to mount into)
sudo mount /dev/hdxX /media/fat32/ -t vfat -o iocharset=utf8,umask=000  (this will mount a fat32 partition hdxX to that folder)

If that works at least you will know that the filesystem is recognised properly, and from there you can try to sort out why it's not being mounted.

---

### Post by buzzohall on 2007-05-31
here is a screen shot of the actual problem occuring i am trying to access the shared drive which is drive E in windows i know for a fact it is formatted with fat32. the 25gb volume is windows, the other is the cd/dvd drive, and the last linux filesystem.

---

### Post by buzzohall on 2007-05-31
1

---

### Post by yabbadabbadont on 2007-05-31
Post the contents of your /etc/fstab file.

---

### Post by buzzohall on 2007-06-07
> **yabbadabbadont said:**
> Post the contents of your /etc/fstab file.


here are the contents of the file in a print screen so that i dont mess any of it up lol

---

### Post by yabbadabbadont on 2007-06-07
I'm going to assume that you would like to mount the drive as /media/windows.  If not, change that path to whatever you like.  Use sudo (for command line editor) or gksudo (graphical editor) to edit your /etc/fstab file.  Add a line like the following:
```
/dev/sda2       /media/windows  vfat        utf8,umask=007,gid=46 0       2
```
Save your changes.  Now open a terminal window and create the mount point (/media/windows).
```
sudo mkdir -p /media/windows
```
Logout and reboot.  It should then be mounted every time you boot.  If you don't want it to be mounted automatically at every boot, then you will need to change the /etc/fstab line to this instead:
```
/dev/sda2       /media/windows  vfat        user,noauto,utf8,umask=007,gid=46 0       2
```
That lets a regular user mount and umount it anytime they like.

---

