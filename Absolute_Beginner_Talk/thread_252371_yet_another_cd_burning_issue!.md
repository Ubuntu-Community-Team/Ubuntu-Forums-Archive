---
title: "yet another cd burning issue!"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Millie on 2006-09-06
Hello

I'm having problems with my cd recorder. I used to have Hoary but have recently upgraded to breezy (I'm waiting for Dapper disk at the mo). Writing CDs never worked with Hoary, but I gave up trying to sort it out hoping that upgrading might fix the issue. It didn't.

I've been looking around the various forums trying to figure out what the problem is. I see that I'm not alone. I used to run Mandrake on this machine (some time ago) and after initial problems with ide-scsi, I was able to write audio CDs.

I moved to Ubuntu because I'd heard it was good. I've done some diagnostics:

1) Issuing cdrecord -scanbus as root

root@yucca:~# cdrecord -scanbus
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-9-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .


2) when a blank cd-r is put into the drive, a CD-ROM icon is displayed on the desktop

3) running cdrecord -checkdrive
root@yucca:~# cdrecord -checkdrive
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-9-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/cdrw'
devname: '/dev/cdrw'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'SONY    '
Identifikation : 'CD-RW  CRX120E  '
Revision       : '1.0j'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R


3) When I try to burn an audio cd, CD/DVD Creator repeatedly prompts me to 'Insert a rewritable or blank disc'. Clicking OK to the message causes the dialogue to be displayed again.

4) When trying to burn and audio cd with Septentine, the following is displayed  in /var/log/messages

Sep  6 21:53:10 localhost kernel: [4301115.171000] cdrom: This disc doesn't have any tracks I recognize!

The disk is ejected and a dialogue box is shown stating 'Writing to disc failed'

5) Issuing dmesg | grep ATAPI gives

[4294675.206000] hdb: SONY CD-RW CRX120E, ATAPI CD/DVD-ROM drive
[4294678.470000] hdb: ATAPI 24X CD-ROM CD-R/RW drive, 2048kB Cache

6) /etc/default/cdrecord looks like the following

#ident @(#)cdrecord.dfl 1.4 02/07/07 copyr 1998 j. schilling
#
# this file is /etc/default/cdrecord
# it contains defaults that are used if no command line option
# or environment is present.
#
# the default device, if not specified elswhere
#
cdr_device=/dev/cdrw

#
# the default speed, if not specified elswhere
#
# note that newer cdrecord versions do not default
# to speed=1. for mmc compliant drives, the default
# is to write at maximum speed, so it in general does
# not make sense to set up a default speed in /etc/default/cdrecord
#
#cdr_speed=40

#
# the default fifo size if, not specified elswhere
#
cdr_fifosize=4m

#
# the following definitions allow abstract device names.
# they are used if the device name does not contain the
# the characters ',', ':', '/' and '@'
#
# unless you have a good reason, use speed == -1 and let
# cdrecord use it's intercal drive specific defaults.
#
# drive name    device  speed   fifosize driveropts
#
teac=           1,3,0   -1      -1      ""
panasonic=      1,4,0   -1      -1      ""
plextor=        1,4,0   -1      -1      ""
sanyo=          1,4,0   -1      -1      burnfree
yamaha=         1,5,0   -1      -1      ""
cdrom=          0,6,0   2       1m      ""

7) Devices are

root@yucca:/dev# ls -latr cd*
lrwxrwxrwx  1 root root 3 2006-09-06 20:06 cdrw -> hdb
lrwxrwxrwx  1 root root 3 2006-09-06 20:06 cdrom -> hdb


I suspect that there is something fundamentally wrong - cdrecord not finding any SCSI devices does not sound good. Should I be loading ide-scsi?
I added ide-scsi to /etc/modules so that it would be loaded at startup, (lsmod says its been loaded) but running a dmesg does not see my cdwriter as a scsi device. Am I barking up the wrong tree here?

I have to say I am very frustrated! Can someone shed any light on this please?!

---

### Post by Millie on 2006-09-08
er, does anyone have any ideas why this is happening?

Any help would be much appreciated!

---

### Post by steve.horsley on 2006-09-08
> **Millie said:**
> er, does anyone have any ideas why this is happening?

Any help would be much appreciated!

Yes. It's because you are using Breezy.

Try using k3b - that one worked for me in Breezy. A very well behaved burner.

---

### Post by Millie on 2006-09-12
Hey, there is someone out there!

Unfortunately, I do not have a permanent internet connection (dialup - sorry) - so I'm reliant on being able to download *small* components. Do you think the CD/DVD Writer in Dapper fixes this? If so, I'll get those disks (sometime).

In the end, I managed to get cdrecord working. There were 2 problems

1) I wasn't calling cdrecord with the correct parameters - here's what I should have used:

Determine the lun etc using 

cdrecord dev=ATAPI -scanbus


Then burn a track using

cdrecord dev=ATAPI:0,1,0 -driveropts=burnfree -v -data /path/to/iso

2) Some of the disks I was using were dodgy - I had some cheap ones (cdrecord identified them as being made by PRINCO) but in the end I used some others branded as being made by memorex (cdrecord identified them as bieng made by RITEK).


Whilst I *can* use the command line (mkisofs, cdrecord etc) - the overall experience isn't good. Even though I've got cdrecord working, cd/dvdrecorder still complains about inserting a writable disk. I've read a lot of posts about cd/dvdrecorder not having the correct permissions. Any idea what they might be? It does sound like some kind of configuration issue.

---

### Post by valmy on 2006-10-23
I'm having the same problem and I'm using Dapper. Anybody has an explanation for this?

---

