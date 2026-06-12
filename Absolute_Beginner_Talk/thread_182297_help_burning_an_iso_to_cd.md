---
title: "help burning an iso to cd"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by CloudyHaze on 2006-05-25
alright, i downloaded a (legal) game.

it is two .iso files

i want to burn each on a cd

now i got to the folder the image is contained in..... right click.....write to disc

it tells me to insert a cd with at least 691mb of freespace

i do(totally new blank cd)

it comes back and tells me the same message

whats up with that?

this is my first attempt at burning a disc on ubuntu

---

### Post by Sef on 2006-05-25
> alright, i downloaded a (legal) game.

it is two .iso files

i want to burn each on a cd

now i got to the folder the image is contained in..... right click.....write to disc

it tells me to insert a cd with at least 691mb of freespace

i do(totally new blank cd)

it comes back and tells me the same message

whats up with that?

this is my first attempt at burning a disc on ubuntu


Are you running Breezy?  It has a bug, and so it does not work right.  It is fixed in Dapper.

---

### Post by CloudyHaze on 2006-05-25
i think im running breezy..

is there a way to check for sure?

---

### Post by Sef on 2006-05-25
System > About Unbuntu   It will tell you what you are running.

---

### Post by CloudyHaze on 2006-05-25
ok im running breezy

now do i have to use dapper to fix my problem or what?

will dapper effect anything else? ie: loaded programs, files(music, work stuff, etc)??

---

### Post by linear on 2006-05-25
If you don't want to upgrade to Dapper just now, you could use GnomeBaker to burn the iso to disk.

---

### Post by CloudyHaze on 2006-05-25
Ok still problems.


Open up GnomeBaker

Go to Actions>Burn CD Image

select the iso file for cd 1

hit ok

the progress screen comes up 

then says fail

the output says:

""cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.12-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'ubuntu-0.8ubuntu1'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'TDK     '
Identifikation : 'CDRW321040X     '
Revision       : 'Df41'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO RAW/R96R
Drive buf size : 4091904 = 3996 KB
Drive DMA Speed: 3225 kB/s 18x CD 2x DVD
FIFO size      : 4194304 = 4096 KB
cdrecord: Success. test unit ready: scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 30 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x30 Qual 0x00 (incompatible medium installed) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 40s
cdrecord: No disk / Wrong disk!
Track 01: data   690 MB         padsize:   30 KB
Total size:      793 MB (78:34.13) = 353560 sectors
Lout start:      793 MB (78:36/10) = 353560 sectors
""

---

### Post by CloudyHaze on 2006-05-25
ok just tried to burn a music cd also

same? error

output reads:

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.12-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 0 = CD-DA
Using libscg version 'ubuntu-0.8ubuntu1'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'TDK     '
Identifikation : 'CDRW321040X     '
Revision       : 'Df41'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO RAW/R96R
Drive buf size : 4091904 = 3996 KB
Drive DMA Speed: 3273 kB/s 18x CD 2x DVD
FIFO size      : 4194304 = 4096 KB
cdrecord: Success. test unit ready: scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 30 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x30 Qual 0x00 (incompatible medium installed) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 40s
cdrecord: No disk / Wrong disk!
pregap1: -1
Track 01: audio   71 MB (07:06.71) no preemp pad     
Track 02: audio   75 MB (07:28.62) no preemp pad     
Track 03: audio   62 MB (06:11.46) no preemp pad     
Track 04: audio  113 MB (11:13.80) no preemp pad     
Track 05: audio   64 MB (06:21.96) no preemp pad     
Track 06: audio   11 MB (01:11.07) no preemp pad     
Track 07: audio   38 MB (03:46.29) no preemp pad     
Track 08: audio  112 MB (11:11.37) no preemp pad     
Track 09: audio   74 MB (07:21.28) no preemp pad     
Track 10: audio   90 MB (08:55.82) no preemp pad     
Track 11: audio   50 MB (05:02.81) no preemp pad     
Total size:      769 MB (76:11.30) = 342848 sectors
Lout start:      769 MB (76:13/23) = 342848 sectors

---

### Post by Mustard on 2006-05-25
It doesnt seem to like the disks you are using.

---

### Post by CloudyHaze on 2006-05-25
lol

really? they are cheap fujifilm cdrs from the drugstore...hehe

work fine on my old computer's really crappy burner

why would they not work on my nice new TDK burner?

---

### Post by Mustard on 2006-05-25
[QUOTE=CloudyHaze]lol

really? they are cheap fujifilm cdrs from the drugstore...hehe

work fine on my old computer's really crappy burner

why would they not work on my nice new TDK burner?[/QUOTE]

I don't know for sure why its not liking them.  I'm just going on what the application output is saying. :)

```
Sense Code: 0x30 Qual 0x00 (incompatible medium installed) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.000s timeout 40s
cdrecord: No disk / Wrong disk!
```

This could also mean that the system is not detecting the disk correctly, I suppose. *shrugs*  I couldn't say for sure.

---

### Post by CloudyHaze on 2006-05-25
ok....trying to figure this out.

i have not really used the cdrom at all since installing linux......

so i decide to see if i can even just play a normal storebought audio cd

nope.....

get this error:

Warning: device /dev/hdc is already handled by /etc/fstab, supplied label is ignored
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Error: could not execute pmount



is there something i just neglected to do in order to properly use my cd rom when i installed ubuntu??????

please help

---

### Post by Mustard on 2006-05-25
From the information above, I'd be interested in seeing the output of dmesg | tail ,just after the failure of the drive to read the CD.
```
dmesg | tail
```
Also it might be interesting to see the contents of the /etc/fstab file.
```
cat /etc/fstab
```

You can enclose the output in these forum codes too [noparse]```
..your code in here..
```[/noparse]

---

### Post by CloudyHaze on 2006-05-25
ok

went to terminal and did 

```
dmesg I tail
```

and got this back

```
[4307319.677000] ATAPI device hdc:
[4307319.677000]   Error: Not ready -- (Sense key=0x02)
[4307319.677000]   Incompatible medium installed -- (asc=0x30, ascq=0x00)
[4307319.677000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4307319.677000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4307321.685000] ATAPI device hdc:
[4307321.685000]   Error: Not ready -- (Sense key=0x02)
[4307321.685000]   Incompatible medium installed -- (asc=0x30, ascq=0x00)
[4307321.685000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4307321.685000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "

```

pluged in

```
cat /etc/fstab
```

and get

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by Mustard on 2006-05-25
Hmm..doing some searches on that output in dmesg, it seems you might have a problematic CD burner.

[http://www.ubuntuforums.org/showthread.php?t=64388](http://www.ubuntuforums.org/showthread.php?t=64388)

Choose some key words from the dmesg output, like 'Incompatible medium installed' and feed them into the search function on the ubuntu forums, and [http://www.google.com/linux](http://www.google.com/linux)  and see if you can dig up some information on how other people solved this problem.  Look for similarities in hardware and brand names so that you can be certain that they are having the same problem.  If you find some links that offer good solutions, but don't understand them, you could post the links in this thread and someone can read over them for you.

Your /etc/fstab looks fine btw.  The dmesg output is definitely showing a problem with the burner not working properly.

This could be a lengthy process, so I would prepare yourself for perhaps solving the issue over a longer period of time.  If your lucky you might find a good solution quite quickly.  The thread I posted has some advice, but I don't know how good it is.

---

### Post by CloudyHaze on 2006-05-25
Thanks much,

appreciate your help :)

---

### Post by Mustard on 2006-05-25
Someone else is having similar output in the logs in this thread too, it might be worth following this thread to see how it pans out too...

[http://www.ubuntuforums.org/showthread.php?t=92790](http://www.ubuntuforums.org/showthread.php?t=92790)

Woops..ignore that..hehehe...it an ancient thread with no verified solution at the end...I forgot I was looking at my last searches that I did with regard to your problem. :)

---

### Post by QueensGambit on 2006-05-31
i have the same problem, tried nautilus,gnombaker,terminal, all says insert cd, but thats with a 3gig iso, 700mb iso works fine, and i have 103gigs free space, i think ubuntu is jelouse im installing fedora

---

