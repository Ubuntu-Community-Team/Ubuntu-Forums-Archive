---
title: "Drive Detection and Partitioning"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by drums907 on 2006-01-15
For some reason the partitioning utility is only seeing 2.1GB of my 15GB harddrive.  This distro looks nice but there is a real glitch in getting it to install properly. :confused: Any thoughts or suggestions for this Linux Newbie would be greatly appreciated.

---

### Post by az on 2006-01-15
[QUOTE=drums907]For some reason the partitioning utility is only seeing 2.1GB of my 15GB harddrive.  This distro looks nice but there is a real glitch in getting it to install properly. :confused: Any thoughts or suggestions for this Linux Newbie would be greatly appreciated.[/QUOTE]
By default, it tries to split an existing partition and install there.  Are you sure that is not what you chose to do?  In that circumstancem it would offer you whater space it can free up from the existing partition.


The second installer option is to blow away an entire drive.  Is that what you want to do?


What options are you being given?

---

### Post by drums907 on 2006-01-15
I am givin the option to erase the entire drive, erase the entire drive and use LVM or manually edit partition table.  The problem is when I erase the entire drive it still comes back and says that the drive is 2.1 GB.  This has caused some trouble with the xserver on this machine as I run out of space.  I am not sure what is working and what is not.

---

### Post by Killerbird on 2006-01-15
I noticed something similar for me too... i selected the option to set up just one big partition and the thing apparently made one partition 500 megs to install the os and what not, and the other one is 18 gigs, and still unformatted...

---

### Post by Sef on 2006-01-17
See if this helps:  When you first to to the partition, highlight the hard disk, then you will have the option erase any partitions that exist.  Then go and partition how you want.

---

### Post by drums907 on 2006-01-17
I have erased all partitions.  I have done all of the different partitioning types in the Guided Partitioning schemes and these do not work.  I have tried changing the BIOS settings.  I have not been able to get the software to recognize the drive Capacity correctly.  It does recognize the correct model and Manufacturer.

---

### Post by shania98 on 2006-01-17
[QUOTE=azz]By default, it tries to split an existing partition and install there.  Are you sure that is not what you chose to do?  In that circumstancem it would offer you whater space it can free up from the existing partition.


The second installer option is to blow away an entire drive.  Is that what you want to do?


What options are you being given?[/QUOTE]
hi, noticed you are on line. can you help me?

---

### Post by dueY on 2006-01-17
[QUOTE=drums907]I have erased all partitions.  I have done all of the different partitioning types in the Guided Partitioning schemes and these do not work.  I have tried changing the BIOS settings.  I have not been able to get the software to recognize the drive Capacity correctly.  It does recognize the correct model and Manufacturer.[/QUOTE]

So you erased all your partitions including any that may have had Windows installed on them?

Just asking because I don't remember if the Ubuntu partitioner detects all available hard drive space or only unformatted/ext2/ext3 space.

---

### Post by az on 2006-01-17
Okay, I think I know what the problem is.  The windows installer can really bork up a partition table.  Did you install linux, install windows and then reinstall linux?  The Windows installer can not reasonably handle a disk with linux partitions on it.

You are going to have to boot the installer and drop to the shell.  (CTRL-ALT-F2)

Use fdisk to print out your partition table.  If it is all screwy, you need to tall fdisk to create a balnk partition table ("m"?  I do not remember right now.)  After that, reboot and try the installer again.  It should be alright.

---

### Post by Iowan on 2006-01-17
I had a similar problem on the box I'm using for a Samba server.  Choosing LVM seemed to bypass the shortcomings of the BIOS.

---

### Post by drums907 on 2006-01-18
EUREKA!!! I Found IT!  There is a clipping jumper for older OSs that was installed on some IDE drives.  Changed the jumper and set for 16 Heads and VOILA!!!!  It is now recognized at full capacity!

---

