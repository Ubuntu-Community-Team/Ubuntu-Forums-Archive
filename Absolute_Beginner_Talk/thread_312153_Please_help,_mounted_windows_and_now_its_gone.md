---
title: "Please help, mounted windows and now its gone"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by pacguy on 2006-12-03
Hi all, I seem to be having a bit of trouble with my windows partition. I mounted it with psychocats tutorial and it should up fine. When I later rebooted the folder on my desktop was gone. I looked around at the various guides and tried to solve the problem by renaming the mkdir and editing the fstab and nothing happened. Sudo mount -a would do nothing. I then tried to install ntfs-3g hoping it might be able to work and now my computer is in more trouble.

fdisk
Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       11937    95883921    7  HPFS/NTFS
/dev/hdc2           11938       14481    20434680   83  Linux
/dev/hdc3           14482       14593      899640    5  Extended
/dev/hdc5           14482       14593      899608+  82  Linux swap / Solaris

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       24321   195358401    7  HPFS/NTFS

This is what I get with fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc2
UUID=904dcd20-dc0d-455f-a1b0-9bfdf60ddd79 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc1
#UUID=CCC89687C8967006 /media/windows     defaults,nls=utf8,umask=007,gid=46 0      1
# /dev/hdd1
#UUID=6C1C20001C1FC44C /media/hdd1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc5
UUID=96320ba2-991d-42ab-afbf-0efe28e4d5c7 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

#/dev/hda2 /media/Windows ntfs nls=utf8,umask=0222 0 0
#/dev/hdc1      /media/windows  ntfs-3g silent,defaults,locale=en_US.utf8 0 0
#/dev/hdd1      /media/windows1 ntfs-3g silent,defaults,locale=en_US.utf8 0 0
#/dev/hdc1      /media/windows  ntfs-3g silent,umask=0,locale=en_US.utf8 0 0
#/dev/hdd1      /media/windows1 ntfs-3g silent,umask=0,locale=en_US.utf8 0 0
/dev/hdc1       /media/windows  ntfs-3g silent,umask=0,locale=en_US.utf8 0 0
/dev/hdd1       /media/windows1 ntfs-3g silent,umask=0,locale=en_US.utf8 0 0


This is my sudo mount -a
Failed to mount '/dev/hdc1': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.


This is what I get when i fun ntfsfix /dev/hdc1
Mounting volume... FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Permission denied
Volume is corrupt. You should run chkdsk.

This is what I get at the end when I install afterbirth nfts-3g using the guide. 
Setting up afterbirth-ntfs-3g (0.0.2-1) ...
/dev/hdc1       /media/windows  ntfs-3g silent,umask=0,locale=en_US.utf8 0 0
You can find your NTFS partition at /media/windows
/dev/hdd1       /media/windows1 ntfs-3g silent,umask=0,locale=en_US.utf8 0 0
You can find your NTFS partition at /media/windows1
fuse
fuse
fuse
fuse
fuse
umount: /dev: device is busy
umount: /proc/bus/usb: device is busy
umount: /var/run: device is busy
umount: /sys: device is busy
umount: /: device is busy
Failed to mount '/dev/hdc1': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.
dpkg: error processing afterbirth-ntfs-3g (--configure):
 subprocess post-installation script returned error exit status 4
Errors were encountered while processing:
 afterbirth-ntfs-3g
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have no idea why the partition that I am not using would be busy and can't figure anything else out. Please help.

---

### Post by kakalaky on 2006-12-03
Have you tried booting into windows and running chkdsk?

---

### Post by pacguy on 2006-12-03
I can't boot into windows because of a crcdisk.sys problem which I am working on now. After using the psychocat guide I was able to view the windows folder and access my files. When I rebooted later on the directory was gone.

---

### Post by kakalaky on 2006-12-03
install ntfsprogs:

```
sudo apt-get install ntfsprogs
```

run ntfsfix:

> ntfsfix /dev/hdc1

---

### Post by pacguy on 2006-12-03
Added ntfsprogs and got this
Setting up afterbirth-ntfs-3g (0.0.2-1) ...
/dev/hdc1       /media/windows  ntfs-3g silent,umask=0,locale=en_US.utf8 0 0
You can find your NTFS partition at /media/windows
/dev/hdd1       /media/windows1 ntfs-3g silent,umask=0,locale=en_US.utf8 0 0
You can find your NTFS partition at /media/windows1
fuse
fuse
fuse
fuse
fuse
fuse
umount: /dev: device is busy
umount: /proc/bus/usb: device is busy
umount: /var/run: device is busy
umount: /sys: device is busy
umount: /: device is busy
Failed to mount '/dev/hdc1': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.
dpkg: error processing afterbirth-ntfs-3g (--configure):
 subprocess post-installation script returned error exit status 4
Errors were encountered while processing:
 afterbirth-ntfs-3g
E: Sub-process /usr/bin/dpkg returned an error code (1)

Then ran ntfsfix /dev/hdc1 and got this again
Mounting volume... FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Permission denied
Volume is corrupt. You should run chkdsk.

That seems bad.

---

### Post by kakalaky on 2006-12-04
Your drive may be failing.  Download Ultimate Boot CD from here:

[http://www.ultimatebootcd.com/download.html]("http://www.ultimatebootcd.com/download.html")

you can test your HD with the tools on it and run chkdsk by selecting NTFS4DOS under Filesystem Tools

---

### Post by pacguy on 2006-12-04
Okay I ran chkdsk like you said and got this screen but I didn't know what to do next.
[http://img.photobucket.com/albums/v112/Pacguy/P1010008.jpg](http://img.photobucket.com/albums/v112/Pacguy/P1010008.jpg)

---

### Post by kakalaky on 2006-12-04
looks like it crashed, what brand of hd do you have the windows install on?

---

### Post by pacguy on 2006-12-04
Its an older western digital one. I'm guessing that makes it an IDE. Anywho its got 120 gb on it and is running ubuntu off of it too. I'm guessing that I may have corrupted the partition then when I made the changes to it.

---

### Post by kakalaky on 2006-12-04
Looks that way, you might want to run the western digital hd diagnostic utility on the ultimate boot cd to make sure there is nothing wrong with the drive.  If it checks out, you will probably have to reformat the windows partition and reinstall.  Make sure you can restore GRUB before you do because the windows install will overwrite the MBR.

---

### Post by pacguy on 2006-12-04
Well thats a bitch. Is there anyone that you can refer me to who might know how to fix this without reinstalling windows.

---

### Post by kakalaky on 2006-12-04
Maybe somebody else here will reply that knows a solution, but I don't know of anybody to send your way.  The evidence is pointing to filesystem corruption, to the point that chkdsk can't fix it.  The only way I know to fix filesystem problems that have gotten that bad is to format the partition.

---

