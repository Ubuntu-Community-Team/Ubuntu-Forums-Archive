---
title: "Since last upgrade USB pen drive wil not mount"
date: 2008-02-06
forum: Apple PPC Users
---

### Post by driven1 on 2008-02-06
I keep getting an error message that the filetype is wrong or that the drive is corrupted, but it works from a live CD, in OS X, and XP. It worked immediately after the install as well, but now I cannot make it mount. I've tried mounting through the terminal also. No joy. Anyone have any ideas?

---

### Post by ajgreeny on 2008-02-06
Filetype is wrong where?  There should be no need to have an entry for a USB drive in /etc/fstab, which is where the file type would perhaps be specified.  Did the drive automount when plugged in before this update, or did you need to do something to mount it?

---

### Post by driven1 on 2008-02-07
After installing from the CD, the usb pen drive worked fine automounting instantly. Then, once I ran the various updates, fixed the sound issues with the powerbook, etc., the usb drive would no longer mount. In the details section of the message it says:

> mount:wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg | tail or so

I ran the dmseg command and it gives a list of numbers such as [783.056421] each folloed by the message usb 2-1: reset low speed USB device using ohci-hcd and address 2

OK, I just tried the dmesg again, now I get something different:

> sdb: Mode Sense:23 00 00 00
sdb: assuming drive cache: write through
SCSI device sdb: 4030464 512-byte hdwr sectors (2064 MB)
sdb: Write Protect is off
sdb: Mode Sense:23 00 00 00
sdb: assuming drive cache: write through
sdb: sdb 1
sd 3:0:0:0: Attached scsi removable disk sdb
sd 3:0:0:0: Attached scsi generic sg1 type 0
FAT: unrecognized mount option "usefree" or missing value

I'm assuming I need to fix the mount option, but I'm not sure where to go to do that.

---

### Post by stream303 on 2008-02-07
How you tried reformatting the pen drive in OSX or Windows?  I've had some sticks give me trouble with manufacturer-formatted sticks until I did this - it was hit or miss.

If a stick had been used in a Vista machine as virtual-memory, it was mandatory.

Once you get it mountable, I like to use gparted as a gui way to reformat my sticks - at least once to get away from the manufacturer's formatting.  This thread is interesting:

[http://ubuntuforums.org/showthread.php?t=468212](http://ubuntuforums.org/showthread.php?t=468212)

---

### Post by driven1 on 2008-02-13
I did reformat it both with Windows and OS X. Neither one helped. This is a real pain because I use  the pen drive to transfer files between Ubuntu, OS X and Windows. It baffles me because it was working fine before, and now it doesn't.

---

### Post by Fernanernie on 2008-02-13
I am also having this issue as well. Stick was formatted in XP SP2

dmesg | tail
```
aj@hellspawn:/$ dmesg | tail
[ 7043.128000] sdb: Mode Sense: 23 00 00 00
[ 7043.128000] sdb: assuming drive cache: write through
[ 7043.128000] SCSI device sdb: 3914752 512-byte hdwr sectors (2004 MB)
[ 7043.132000] sdb: Write Protect is off
[ 7043.132000] sdb: Mode Sense: 23 00 00 00
[ 7043.132000] sdb: assuming drive cache: write through
[ 7043.132000]  sdb: sdb1
[ 7043.172000] sd 3:0:0:0: Attached scsi removable disk sdb
[ 7043.172000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 7044.136000] FAT: Unrecognized mount option "usefree" or missing value
 

```
sudo fdisk -l
```
aj@hellspawn:/$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82688268

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6009    48267261    7  HPFS/NTFS
/dev/sda2            6010       14237    66091410   83  Linux
/dev/sda3           14238       14593     2859570    5  Extended
/dev/sda5           14238       14593     2859538+  82  Linux swap / Solaris

Disk /dev/sdb: 2004 MB, 2004353024 bytes
255 heads, 63 sectors/track, 243 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d461f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         243     1951866    6  FAT16


```
sdb1 is USB drive
lsusb

```
aj@hellspawn:/$ lsusb
Bus 003 Device 003: ID 0930:6545 Toshiba Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

Properly shows up on Bus3 Device 3

System > Preferences > Removable Drives and Media > First 3 checkmarked 

No entry in fstab (has never needed it before)

---

### Post by stream303 on 2008-02-14
Looks like a quick trip to gconf-editor can restore it:  (gets rid of that "usefree" error)

[http://ubuntuforums.org/showthread.php?p=3575602](http://ubuntuforums.org/showthread.php?p=3575602)

Let's see how this plays on ppc!

---

### Post by driven1 on 2008-02-18
> **stream303 said:**
> Looks like a quick trip to gconf-editor can restore it:  (gets rid of that "usefree" error)

[http://ubuntuforums.org/showthread.php?p=3575602](http://ubuntuforums.org/showthread.php?p=3575602)

Let's see how this plays on ppc!

This worked perfectly. Thanks for the help. Not sure how to make the official thanks tool work.:confused:

---

