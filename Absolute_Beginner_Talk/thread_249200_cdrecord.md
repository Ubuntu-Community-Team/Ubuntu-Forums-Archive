---
title: "cdrecord"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by prillid on 2006-09-02
Hi all,
have a problem.
The basic Gnome CD/DVD Creator in Ubuntu 6.06 does not work. When I press on the button Write to Disk the appearing window demands Insert a rewritable or blank disk although the blank disk is in the CD-R/RW-drive.
The problem with burning CD is in Ubuntu 5.10 and Kubuntu 6.06 too.
I think that the programm "cdrecord" does not see the CD-R/RW-drive, i.e. it is not emulation ATAPI-drive to scsi-drive, perhaps. It follows from the following.
When I give command:
$ sudo cdrecord -scanbus
I get:

Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-23-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: 'ATAPI:'
devname: 'ATAPI'
scsibus: -1 target: -1 lun: -1
Warning: Using ATA Packet interface.
Warning: The related Linux kernel interface code seems to be unmaintained.
Warning: There is absolutely NO DMA, operations thus are slow.
cdrecord: No such file or directory. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .


But command:
$ sudo cdrecord dev=/dev/hdd -scanbus
shows:

Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-23-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus1:
        1,0,0   100) *
        1,1,0   101) 'SAMSUNG ' 'CD-R/RW SW-248B ' 'R501' Removable CD-ROM
        1,2,0   102) *
        1,3,0   103) *
        1,4,0   104) *
        1,5,0   105) *
        1,6,0   106) *
        1,7,0   107) *

The problem is not hardware related because the "cdrecord" works fine in other Linux on the same mashine.
I tried some advices from this forum but unsuccessfully.
Sorry for my English.

---

### Post by Stone123 on 2006-09-02
First of all :
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

Then paste  ls -l /dev/sg*
and : ls -l /dev//hdd

i think if there is /dev/sg0 you should do:
sudo chown root:cdrom /dev/sg0 

Then again it can be buggy program.

---

### Post by steve.horsley on 2006-09-02
Oddly, I have had no problens with CD burning in 6.06, on either of the two machines I have installed it on.

However, whenever I have problems with CD burning, I always resort to using k3b, which always seems to cope better when unexpected things are happening. So I suggest you try installing k3b.

---

### Post by prillid on 2006-09-02
2 Stone123

Thank you for your suggestions. I have done all but without success.
In hdparm /dev/hdd
                  was written
                             using_dma = 1 (on)

and I add script in the end of hdparm.conf too.

When I paste: ls -l /dev/sg*
I get: No such file or directory  

and
ls -l /dev/hdd
shows:
brw-rw---- 1 root cdrom 22, 64 2006-09-02 22:21 /dev/hdd


2 Steve.horsley

I tried k3b in Kubuntu 6.06. It`s a front-end for programm "cdrecord" and result was bad too.

---

### Post by steve.horsley on 2006-09-02
Hmm. I'm out of my depth here, I'm afraid. All I can say is that I believe that since Dapper, IDE CDROM drives no longer need SCSI emulation. On the laptop I'm currently on, **sudo cdrecord -scanbus** doesn't find any drives. However, **ls -l /dev/cdrom** shows that /dev/cdrom is actually a symlink to /dev/hdc. And I am able to record CDROMs (using the GUI front ends - I don't know what ID is passed to the cdrecord backend).

---

### Post by Stone123 on 2006-09-02
you might take a look at this thread:

[http://www.ubuntuforums.org/showthread.php?t=217472&highlight=burning+issues](http://www.ubuntuforums.org/showthread.php?t=217472&highlight=burning+issues)

---

