---
title: "How do I backup DOS 6.2 files to a CD-ROM from Ubuntu?"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by LGM on 2008-02-04
My HD is set-up with two primary partitions and an extended partition.
The first partition, (2 GIG), is formatted FAT16 and has DOS 6.2 installed.
The second partition, formatted FAT32, has Win98se installed.
The extended partition for Ubuntu has Dapper Drake 6.06
 
I use the GRUB boot loader and can access and run each opsys.  
My current concern is making backups of my files in each O.S. on CDs.
 
The CD Creator software that is part of Dapper works fine for backing up my Ubuntu data, and I can install Roxio on Win98se.  However, for stand-alone DOS 6.2 I haven't found any burning software that runs from the command prompt.  
 
My first question is: Can I access the DOS filesystem from Ubuntu without corrupting the DOS partition?  How do I do it?
 
When running Dapper, the pull-down menu choice for 'Computer' lists the following:
Floppy Drive
CD-RW Drive
MS-DOS 6
WIN08SE
Filesystem
 
From this menu I'm able to mount the floppy drive but I'm not able to mount the MS-DOS or WIN98se partitions -- the system says they are inaccesable.  What do I need to do? 
 
Once I have the MS-DOS filesystem mounted can I then use copy to paste DOS files into the CD Creator window without corrupting the MS-DOS partition?  
 
Does my mount command need to specify info about the FAT16 filesystem before Dapper can read it?

---

### Post by hardyn on 2008-02-04
drop to the command line...

sudo mkdir /media/dos
sudo mkdir/media/win98
sudo mount /dev/hdax /media/dos
 (dos parition, may be sda dont recall which one dapper used)
sudo mount /dev/hdax /media/win98
 (windows parition, may be sda dont recall which one dapper used)

you should then be able to burn them as usual.

then 
sudo umount /media/dos
sudo umount /media/win98
sudo rmdir /media/dos
sudo rmdir /media/win98
 (if you wont use them again)

---

