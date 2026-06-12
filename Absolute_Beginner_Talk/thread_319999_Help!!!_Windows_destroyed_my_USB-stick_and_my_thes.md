---
title: "Help!!! Windows destroyed my USB-stick and my thesis"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by Campitor on 2006-12-16
Help:

   I've been writting my thesis on LyX.  I backed up all my files on a new SanDisk USB flash drive (2GB) and went home for the holidays.  When I go to my mom's computer to work, I try to copy one file onto de USB flash drive and Windows collapsed.  After a reboot, I insert my flash drive and I get:  Removable disk is not formatted.

  I panic....scream a bunch of times and then pop-out my ubuntu disk.  Pop it into the computer and boot on the live cd.  I try accessing the drive, but Linux won't recognize de drive.  If I do:

 sudo mount -t vfat /dev/sda1 ./temp  #I created the dir temp just to check

I get:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

After doing: dmesg | tail .... i get:

sda: assuming drive cache: write through
SCSI device sda: 4001760 512-byte hdwr sectors (2049 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
 sda: sda1
sd 4:0:0:0: Attached scsi removable disk sda
usb-storage: device scan complete
FAT: invalid media value (0x01)
VFS: Can't find a valid FAT filesystem on dev sda1.

I remember there used to be a way to add the file system to the superblock with mkfs, but I'm afraid I'll format the hole thing and I may loose some of my thesis chapters.  I really need help....maybe I can recover something.  I didn't erase anything, nor moved anything out.  I have the original files, but they are 2500 miles away from here, and I need to finish one chapter before January 8th.  Please...any help would be greatly appreciated ..

Camp

---

### Post by bodhi.zazen on 2006-12-16
Try test disk:

[Advanced FAT Repair](http://www.cgsecurity.org/wiki/Advanced_FAT_Repair)

[Test Disk wiki](http://www.cgsecurity.org/wiki/TestDisk)

[Test disk download (versions for Windows and Linux)](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by houstonbofh on 2006-12-16
In your case I would recommend finding a local data recovery company.  Learning how to fix a corrupt file system is slightly beyond the nubie forum.

---

### Post by floke on 2006-12-16
What about Knoppix. Would this be of any use?

---

### Post by Campitor on 2006-12-16
> **bodhi.zazen said:**
> Try test disk:

[Advanced FAT Repair](http://www.cgsecurity.org/wiki/Advanced_FAT_Repair)

[Test Disk wiki](http://www.cgsecurity.org/wiki/TestDisk)

[Test disk download (versions for Windows and Linux)](http://www.cgsecurity.org/wiki/TestDisk_Download)

Thank you...thank you....thank you....thank you....  The Test Disk utility fixed the USB stick, and I was able to copy all the files into the hard drive, another USB stick, a Zip file, email them to my gmail account, and yes....another USB stick.

thank you very much.  I can breath again.  That Utility should be included into ubuntu base...it's a life saver.  I was too nervous to write up what I did, but I basically followed the menu, and re-wrote the BS (boot sector for FAT 32).  

Now to install Ubuntu on my mom's machine, and back to work.

Did I mention?  Thank you very much!!!!!  I love these forums!!!!! I love UBUNTU.... I hate MS-Windows...I hate it.

Camp.

PS.  I think re-building a boot sector should be part of the newbie forum...cause I really didn't know hwere to turn.

---

