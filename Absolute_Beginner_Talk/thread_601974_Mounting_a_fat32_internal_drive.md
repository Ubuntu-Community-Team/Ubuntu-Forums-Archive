---
title: "Mounting a fat32 internal drive"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Rbchound on 2007-11-03
I have installed Ubuntu 64 which is working fantastic.
I need to have access to my photo archive which is on another internal drive.
The drive is fat 32.
I want to have read/write access to the drive and be able to see it at start up.
I am an extreme newbe when it comes to command line and could really use your help.
The drive is  /dev/sdc1.
What steps do I need to take?  I know how to get into the terminal but thats about it.

Please help.

---

### Post by Pumalite on 2007-11-03
sudo mkdir /media/fat32
sudo mount -t fat32 /dev/sdc1 /media/fat32

---

### Post by Rbchound on 2007-11-03
thanks pumalite,

Do I need to add anything in fstab for read/write access and for automounting at bootup?

---

### Post by ddrichardson on 2007-11-03
You can add the mount line to /etc/fstab for automounting, you shouldn't need to specify rw as I believe vfat is defaulted to rw.

Incidentaly, I thought the file system type was vfat and not fat32. Live and learn I guess.

---

### Post by Pumalite on 2007-11-03
They are both one and the same.

---

### Post by ddrichardson on 2007-11-03
I know they are the same, just didn't know mount recognised it, it isn't even mentioned as a valid filesystem type in the man page. Like I said - live and learn ;-)

---

### Post by Duck2006 on 2007-11-03
So the line in the fstab sould look some thing like this.

/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0

---

