---
title: "Drive mounting issues."
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by richardporter on 2007-08-25
I'm a relative newbie when it comes to linux and infact Ubuntu, but have got on okay setting it up with the exception of this problem. Please bare with my lack of Ubuntu-based-knowledge!

I have three drives installed in my computer, an IDE drive which is the boot partition, and two sata drives - sda and sdb. These have been formatted with gparted to ext3. What i would like to do, is get them to mount automatically when i boot up with write privileges.

From the forum searching i've been doing, i understand that its something to do with a fstab file ?

As each thread i've read has differed slightly, as has the recommended solution - none of which have yet worked for me. So i thought i'd put it out there and see if anyone might be able to help my individual situation.

Many thanks in advance for any help you might be able to give

regards

Rich

---

### Post by uclalinux on 2007-08-25
in the terminal type the following
1. sudo -i
2. nano /etc/fstab

open another terminal
1. sudo -i
2. vol_id -u /dev/sda1
3. vol_id -u /dev/sdb1

back in the fstab file you need to add thouse two hdd

using this 

UUID="that long number the vol_id, just copy paste it (linux uses Ctrl+insert, not ctrl+V to paste)"

let me redo that

UUID="that number"   /"path to were to mount it"  ext3  defaults 0 2  


you will first need to make files where you want to mount the hard drives, 
for that you need to 

mkdir /"where you want to mount them"   (I did mine in /home/matt/sdb1), but you can mount them anywhere you want. you can call the file first_drive & second_drive
after you made the folders you need to modife there owner

chown "username":"username" /"path to file"

then when is all done 

type, 
mount -a 

all should work. :) 

here is a copy of mine for reference


*************
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=5580371c-196a-4b6c-80e0-746c38766c8b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0adcee77-202e-484f-961d-b073478adbea /boot           jfs     defaults        0       2
# /dev/sda1
UUID=F29014B9901485EF /home/matt/windows_partion     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=e2cd600a-6c8e-4af5-87a7-713b020eb22d /home/matt/sdb1     ext3    defaults        0       2
# /dev/sda7
UUID=2fd82c5c-d2e8-4456-9dc9-416ed1e6a54c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by richardporter on 2007-08-25
problem resolved! great explanation that even i could understand!

many thanks

rich

---

### Post by Kedaeus_Sendre on 2007-08-27
> **richardporter said:**
> problem resolved! great explanation that even i could understand!

many thanks

rich

**Word!** I second that.

This thread needs to be stickied, highlighted, and underlined! 

Most people want to mount NTFS drives with read, write, execute abilities and all kinds of other crap.. It's impossible to find any information on mounting an ext3 drive that is readable and easily understood. 

For the past few weeks i've been manually executing a script to mount my HDD's every time I boot my system. Everything else I have tried has failed. 

-Ked

---

### Post by dmber on 2007-09-03
i'm getting a 

-bash: vol_id: command not found

error when trying to follow the instructions.

---

