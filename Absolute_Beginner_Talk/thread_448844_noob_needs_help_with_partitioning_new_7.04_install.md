---
title: "noob needs help with partitioning new 7.04 install on old PC"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by LifeIsShort on 2007-05-19
to anyone who might be able to assist...

trying to partition a new hard drive for a linux only installation of Ubuntu v 7.04 on an old PC (7yrs old)
PC is an HP pavillion 900 MHz pantuim III
previous HDD died (40GB) and I replaced with a Seagate 320 GB HDD

I am getting a GRUB error 18

read posts suggesting partition some small amount for a /boot partition, but having much difficulty with this seemingly simple task.

please assist

please note I am NOT trying to dual boot any other OS

I really wish to stay strictly on Linux.

thanks in advance

---

### Post by ntetreau on 2007-05-19
Hi, you are right about the fixing your problem with a smaller /boot partition.  I am copy/pasting the relevant info here for others who might get the same problem:

Error 18

Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

The kernel it self does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem. 


As for a fix, the easiest would be to reinstall using the LiveCD.  When the installer ask about automatic partionning, choose "Custom partitioning", then gparted will start and you can create your own partitions.  I always create 3 ext3 partitions.  The first is /boot (250MB), the second is / (called root) of 12-15gigs, and the rest is /home.  The rest of the install is the same.  

Hopefully, this will fix your problems.

Nic

---

### Post by LifeIsShort on 2007-05-20
created partitions as described....

250MB for /boot
15000MB for /
2MB for swap

I did not have the option of configuring the partitions in the configuration you described.

the result was not so good unfortunately...

boot failed please insert boot disk

any help would be much appreciated.

---

### Post by LifeIsShort on 2007-05-20
sorry, 2 GB for swap

---

### Post by ntetreau on 2007-05-20
But did you redo the whole installation?  It seems that grub is not installed... Also, you may already have it but I guess you need a /home partition as well, probably with all the remaining disk.  However, it just seems at the moment that grub is not installed for the error message,

Nic

---

### Post by LifeIsShort on 2007-05-20
I redid the entire install, found some mistakes....fixed them...then restarted without liveCD...

same thing, disk error

then I restarted with liveCD and checked logs...

I found this...not sure if it means anything though...other than these are the last few lines in the messages log...

May 21 00:09:18 ubuntu kernel: [  537.040000] kjournald starting.  Commit interval 5 seconds
May 21 00:09:18 ubuntu kernel: [  537.040000] EXT3 FS on hda1, internal journal
May 21 00:09:18 ubuntu kernel: [  537.040000] EXT3-fs: mounted filesystem with ordered data mode.
May 21 00:09:18 ubuntu kernel: [  537.364000] kjournald starting.  Commit interval 5 seconds
May 21 00:09:18 ubuntu kernel: [  537.364000] EXT3 FS on hda2, internal journal
May 21 00:09:18 ubuntu kernel: [  537.364000] EXT3-fs: mounted filesystem with ordered data mode.
May 21 00:09:47 ubuntu gconfd (root-8446): GConf server is not in use, shutting down.
May 21 00:09:47 ubuntu gconfd (root-8446): Exiting
May 21 00:22:04 ubuntu -- MARK --

one other thing.....

I was unable to allocate the remaining 300GB, I kept getting an error message saying I can not start the end before the beginning.


I plan on bringing the PC to work to have a friend help me out, but willing to take any advice I can get...

I'm sure I only gave you more questions, but like the post is titled...I'm new to this OS and filesystem...

Jay

---

### Post by ntetreau on 2007-05-22
I had this problem before where the "end cannot start before the beginning" kind fo thing.  I fixed it by creating a smaller partition, let's say 100Gigs or less, applying the changes, then resizing it to 300gigs.  

While you install, is grub installed on /dev/hda (there is a screen at the end of the install config if i remember well)?

 You can also try to reinstall your grub manually using this [howto]("http://doc.gwos.org/index.php/Restore_Grub") (I haven't tried this myself) 

Also, try to boot the liveCD and choose boot from hard disk.

Nic

---

### Post by LifeIsShort on 2007-05-23
Nic,

Thank you for all of your advice and help. As it turns out the hard drive I installed was pre-formatted for a Windows system. I mistakenly assumed a "bare drive" purchased meant it was truly "bare"

A friend who is quite savvy with Linux manually re-formatted the drive and then we re-installed the 7.04 OS from the beginning again....

I'm off and running now completely free of the "other Operating System" we all know and dislike!!:D

Coming from a Unix environment at work I should quickly adapt to Linux....I just have to get some practice on application installation here in Ubuntu. 

so far so good!!!

Again, thanks for the assistance and advice..

Jason,

"Nam et ipsa scientia potestas est"
Knowledge is power. - Francis Bacon

---

