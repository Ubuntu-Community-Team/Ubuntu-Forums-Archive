---
title: "I Lost everything on hard drive, or have I???"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2007-02-27
I was following the instructions at [psychocats]("http://psychocats.net/ubuntu/separatehome") to make a seperate home partition and while the resizing process was going on using gparted I clicked on the details button while the /dev/hda1 resizing was going on. Suddenly, I got an error that one of the partions was mounted and all progress was stopped. Nothing I could do to make it continue so I backed out.
I booted to my gparted live cd and this is what is left:
/dev/hda  (149.05 GB)
/dev/hda1 **unknown** (147.61 GB) .......boot   ......this _**was**_ my ext3 partition 
/dev/hda2 extended (1.44 GB)
/dev/hda5 swap  (1.44GB)
/dev/hda3 **unknown** (0.00) GB  This is the partition** I intended to be** /home (35GB)

gparted is not showing any portion of hda1 as being used which is really worrysome. On that partion I have a complete tar backup of the system but I have no idea of how to access it.

This is what I have left:
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   309556484   154778211   83  Linux
/dev/hda2       309556485   312576704     1510110    5  Extended
/dev/hda3       312576705   312576705           0+  83  Linux
/dev/hda5       309556548   312576704     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    78043769    39021853+   7  HPFS/NTFS
/dev/hdb2        78043770    78156224       56227+   f  W95 Ext'd (LBA)
ubuntu@ubuntu:~$

I need help in a big time way.
Peter

---

### Post by confused57 on 2007-02-27
Maybe checking the filesystem on the partition would help:

[http://www.ubuntuforums.org/showpost.php?p=2198398&postcount=2](http://www.ubuntuforums.org/showpost.php?p=2198398&postcount=2)

---

### Post by kindafunnylookin on 2007-02-27
Unknown--that is how it is listed in gparted. It used to be ext3.
Peter

---

### Post by kindafunnylookin on 2007-02-27
bump

---

### Post by bodhi.zazen on 2007-02-27
The only trick I have is cfdisk.

From the live CD, fire up cdisk, and make a new linux partition in the unallocated sapce.

cfdisk: [http://www.linux.org/docs/ldp/howto/IBM7248-HOWTO/cfdisk.html](http://www.linux.org/docs/ldp/howto/IBM7248-HOWTO/cfdisk.html)

Then try to mount it.

DO NOT FORMAT IT.

If that fails, try test disk.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

I do not know if TestDisk is on the Ubuntu live CD, but it is on the gparted live CD :

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Download: [Download Gparted](http://sourceforge.net/project/downloading.php?groupname=gparted&filename=gparted-livecd-0.3.3-7.iso&use_mirror=osdn)

HTH

---

### Post by george29 on 2007-02-27
you could also look at this page

[http://servers.linux.com/article.pl?sid=06/08/21/1558230&from=rss](http://servers.linux.com/article.pl?sid=06/08/21/1558230&from=rss)

might be useful - do a forum search for recovering files..

.............................................................................

now for the moralistic point - you said you had a system backup... unfortunate that you decided to keep it on the partition that it was a back up of! 

if you are going to keep a tar backup, then it's best to either archive it to DVD, an external hard drive or a different internal drive. not much point having it otherwise!

---

### Post by kindafunnylookin on 2007-02-27
Thank you guys for your efforts. Nothing suggested worked for me so at this point I am going to format the disk and then partition the disk (correctly this time) and then reinstall Dapper instead of Edgy. I think Dapper is where I belong given the skills that I posess. Most of my /home info is on an external HD - I was just hoping to restore the entire edgy system.

---

