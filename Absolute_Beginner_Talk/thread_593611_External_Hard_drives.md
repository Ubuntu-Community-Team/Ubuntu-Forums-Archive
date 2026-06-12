---
title: "External Hard drives"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Cpt Black on 2007-10-27
Hi,

I've recently changed from windows vista to ubuntu 7.04 and am having slight problems using my external hard drives with data stored on there from vista. The file system of the hard drives is ntfs.

I have installed ntfs-3g and have it working where I can mount a hard drive to a folder in /mnt/<hd name>

I would like to set it up so when I plug in the hard drive, it mounts automatically to a folder with a given name. Currently, I have to check with gparted to find out which hard drive is in which sd slot and mount each in the terminal.

Any help or thoughts on this would be greatly appreciated.

Cheers,
CB

---

### Post by vanadium on 2007-10-27
External removable drives do automatically mount under /media in Ubuntu. An icon appears on the desktop. In the terminal, you will find it under /media/nome_of_drive. If you want the drives each time to mount under a name of your choosing, then just set a volume label. How this is done, depends on the file system.Details are here: [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive) or [http://www.debuntu.org/device-partition-labeling](http://www.debuntu.org/device-partition-labeling)

---

### Post by Cpt Black on 2007-10-27
Ah ha, that works perfectly, cheers.

I used the first link because it had the ntfs file system on it. It appears all to be fine now.

Cheers,
CB

---

