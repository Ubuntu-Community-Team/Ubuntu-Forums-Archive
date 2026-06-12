---
title: "cdrw not recognized"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Shortspan on 2008-02-05
I have been using various live CDs for almost a year now and have not had an issue with the OP Sys using my TDK Cdrw.  It has always worked fine.  But I decided to hard load Ubuntu (and now Mint to try and resolve the problem) but Linux will not recognize the TDK Cdrw.  I have a dual boot system with Win2000 on the other partition.  The grub boot works fine, which will load into Ubuntu (Mint) by default or Win2000 by selection.  I also have a LiteOn DVD player  which is recognized and plays discs just fine.  Both drives are ATA IDE not SATA.
Why will the CDRW work fine with the live distributions (many other distros, not just Ubuntu) but will not work with a full install??? I may also have a few permission issues.
Using hdparm I get the following from the drive:

mike@mike-desktop:~$ sudo hdparm /dev/hdd

/dev/hdd:
 IO_support    =  1 (32-bit)
 unmaskirq     =  1 (on)
 using_dma     =  0 (off)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
mike@mike-desktop:~$ 

Am I wrong or does there seem to be a wrong I/O controller for the Cdrw device?
If so how does one correct this?
Also, I got a list of permissions for the Media file and got this:

mike@mike-desktop:/media$ ls -l
total 16
lrwxrwxrwx 1 root root       6 2008-02-05 04:28 cdrom -> cdrom0
drwxr-xr-x 2 root root    4096 2008-02-05 04:28 cdrom0
drwxr-xr-x 2 root root    4096 2008-02-05 04:28 cdrom1
lrwxrwxrwx 1 root root       7 2008-02-05 04:28 floppy -> floppy0
drwxr-xr-x 2 root root    4096 2008-02-05 04:28 floppy0
drwxrwx--- 1 root plugdev 4096 2008-02-03 19:50 hda1
mike@mike-desktop:/media$ 

The Cdrw drive in question (faulty one) is "cdrom0".  
Any suggestions would be helpful.  I'm new to troubleshooting.

Thanks;  Michael

---

### Post by dcstar on 2008-02-05
> **Shortspan said:**
> 
.........
The Cdrw drive in question (faulty one) is "cdrom0".  
Any suggestions would be helpful.  I'm new to troubleshooting.



Make sure (do NOT assume) that all the jumpers on your IDE devices are correct.

Ubuntu identifies IDE devices in the following way:

/dev/hda - IDE Channel 1 Master
/dev/hdb - IDE Channel 1 Slave
/dev/hdc - IDE Channel 2 Master
/dev/hdd - IDE Channel 1 Slave

Make sure there are correct Master/Slave settings (no incorrect "Cable Select" stuff), and NO "Slave only" devices on a channel.

---

### Post by Shortspan on 2008-02-06
dcstar:
     Thanks for the response.  I tired changing the connections/ jumpers in every combination that made sense, but it still isn't recognizing any cds.   The drive is listed as a cdrom or cdrom1 depending on how I configure.  I even moved the drives around (from primary IDE to secondary IDE ).  I checked BIOS and reset some settings but nothing.  When I boot into Win2000, the drive is always recognized and operates just fine.  For some reason Ubuntu/ Mint doesn't like this drive even though it works fine in live CD mode. 
Just a note.  For some reason my permission issues have disappeared, finally.  I disabled the need for permissions a while ago but it took a couple of boots for it to take effect I guess?  Perhaps my installation or this distro volume has a few issues?  Almost everything else works great.  Like me, I guess its a work in progress!

---

