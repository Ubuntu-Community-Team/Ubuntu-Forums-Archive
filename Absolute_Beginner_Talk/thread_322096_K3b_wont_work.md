---
title: "K3b wont work"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by Linux&amp;Lizards on 2006-12-20
Hey everybody!

:rolleyes:  every time I try to burn a device with k3b I get this  
Unable to send CUE sheet this may be caused by the wrong settings.

I am using edgy any ideas on how to fix this?
I really need to get this working

---

### Post by Linux&amp;Lizards on 2006-12-20
jeez this is flippin retarded.
normally you guys are just brimming with suggestions.

---

### Post by ramjet_1953 on 2006-12-20
Try running K3b by going into a terminal an typing sudo K3b.

Regards,
Roger 8)

---

### Post by LookTJ on 2006-12-20
What cd drive you have?

---

### Post by scxtt on 2006-12-20
i had a problem w/ k3b and bin/cue (also same problem in GnomeBaker) -- problem was in the .cue file, it was using all CAPS for the filename when the file was in all lowercase ...

and if you're gonna sudo a GUI app, use kdesu or gksu ...

---

### Post by Linux&amp;Lizards on 2006-12-20
this is what I got when I stuffed it in a terminal

 mcmahon@mcmahon-desktop:~$ sudo k3b
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ERROR: Communication problem with k3b, it probably crashed.
mcmahon@mcmahon-desktop:~$


Jeez I'm kinda at a loss of what to do.

---

### Post by TooRight on 2006-12-20
It would be simple enough to do a reinstall... grab Automatix and it'll do it for ya even!!

---

### Post by wpshooter on 2006-12-20
> **Linux&Lizards said:**
> Hey everybody!

:rolleyes:  every time I try to burn a device with k3b I get this  
Unable to send CUE sheet this may be caused by the wrong settings.

I am using edgy any ideas on how to fix this?
I really need to get this working

Did it work at some point in time and then start displaying this behavior or has it been doing the ever since it was installed ?

Thanks.

---

### Post by Linux&amp;Lizards on 2006-12-20
2 things.
automatix is currently down :(
and secondly, I recently reinstalled edgy and it didn't work then.
its used to work in pclinuxos but a week ago I was having problems because it couldn't find the right executables.

---

### Post by Linux&amp;Lizards on 2006-12-20
my apologies, automatix is working again sorry for bad info.

---

### Post by Linux&amp;Lizards on 2006-12-20
heres the outpt from gnomebaker



cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.17-10-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identifikation : 'DVD-RW  DVR-110D'
Revision       : '1.17'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0016 
Profile: 0x0015 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 4194304 = 4096 KB
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Turning BURN-Free off
Performing OPC...
cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 0E 93 00 00 0E 26 09 31 FE 08 01 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x01 (logical unit communication time-out) Fru 0x0
Sense flags: Blk 244514816 (not valid) 
resid: 63488
cmd finished after 2.428s timeout 40s
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.

write track data: error after 0 bytes
Writing  time:   18.082s
Average write speed 585.1x.
Fixating...
cdrecord: Success. close track/session: scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0E 00 00 00 00 64 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x64 Qual 0x00 (illegal mode for this track) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.006s timeout 480s
cmd finished after 0.006s timeout 480s
Fixating time:    2.214s
cdrecord: Cannot fixate disk.
cdrecord: fifo had 64 puts and 1 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

---

### Post by Linux&amp;Lizards on 2006-12-20
this is the log from another disk burning ap



imager (BraseroLocalImage) set_output
job (BraseroLocalImage) set_task
imager (BraseroLocalImage) get_track
job (BraseroLocalImage) set_task
Session starting:
	flags			= 16727 
	media type	= 0
	speed		= 37
	track type		= 8
	track format	= 2
	output		= none
job (BraseroCDRecord) set_rate
recorder (BraseroCDRecord) set_drive
recorder (BraseroCDRecord) set_flags
job (BraseroCDRecord) set_source
job (BraseroCDRecord) set_task
recorder (BraseroCDRecord) record
process (BraseroCDRecord) getting varg
cdrecord (BraseroCDRecord) set_action
process (BraseroCDRecord) got varg:
	cdrecord
	-v
	dev=/dev/hdc
	gracetime=0
	speed=37
	driveropts=burnfree
	-dao
	fs=16m
	-data
	-nopad
	/home/mcmahon/Desktop/Distros/livecd-i686-installer-2006.1.iso
process (BraseroCDRecord) launching command
process (BraseroCDRecord) stderr: cdrecord: Warning: Running on Linux-2.6.17-10-generic
process (BraseroCDRecord) stderr: cdrecord: There are unsettled issues with Linux-2.5 and newer.
process (BraseroCDRecord) stderr: cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
process (BraseroCDRecord) stderr: scsidev: '/dev/hdc'
process (BraseroCDRecord) stderr: devname: '/dev/hdc'
process (BraseroCDRecord) stderr: scsibus: -2 target: -2 lun: -2
process (BraseroCDRecord) stderr: Warning: Open by 'devname' is unintentional and not supported.
process (BraseroCDRecord) stderr: Linux sg driver version: 3.5.27
process (BraseroCDRecord) stderr: cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
process (BraseroCDRecord) stderr: SCSI buffer size: 64512
process (BraseroCDRecord) stderr: cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
process (BraseroCDRecord) stderr: cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
process (BraseroCDRecord) stdout: Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
process (BraseroCDRecord) stdout: NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
process (BraseroCDRecord) stdout:       and thus may have bugs that are not present in the original version.
process (BraseroCDRecord) stdout:       Please send bug reports and support requests to <cdrtools@packages.debian.org>.
process (BraseroCDRecord) stdout:       The original author should not be bothered with problems of this version.
process (BraseroCDRecord) stdout: 
process (BraseroCDRecord) stdout: TOC Type: 1 = CD-ROM
process (BraseroCDRecord) stdout: Using libscg version 'debian-0.8debian2'.
process (BraseroCDRecord) stdout: Driveropts: 'burnfree'
process (BraseroCDRecord) stdout: atapi: 1
process (BraseroCDRecord) stdout: Device type    : Removable CD-ROM
process (BraseroCDRecord) stdout: Version        : 0
process (BraseroCDRecord) stdout: Response Format: 2
process (BraseroCDRecord) stdout: Capabilities   : 
process (BraseroCDRecord) stdout: Vendor_info    : 'PIONEER '
process (BraseroCDRecord) stdout: Identifikation : 'DVD-RW  DVR-110D'
process (BraseroCDRecord) stdout: Revision       : '1.17'
process (BraseroCDRecord) stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
process (BraseroCDRecord) stdout: Current: 0x0009
process (BraseroCDRecord) stdout: Profile: 0x002B 
process (BraseroCDRecord) stdout: Profile: 0x001B 
process (BraseroCDRecord) stdout: Profile: 0x001A 
process (BraseroCDRecord) stdout: Profile: 0x0016 
process (BraseroCDRecord) stdout: Profile: 0x0015 
process (BraseroCDRecord) stdout: Profile: 0x0014 
process (BraseroCDRecord) stdout: Profile: 0x0013 
process (BraseroCDRecord) stdout: Profile: 0x0011 
process (BraseroCDRecord) stdout: Profile: 0x0010 
process (BraseroCDRecord) stdout: Profile: 0x000A 
process (BraseroCDRecord) stdout: Profile: 0x0009 (current)
process (BraseroCDRecord) stdout: Profile: 0x0008 
process (BraseroCDRecord) stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
process (BraseroCDRecord) stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
process (BraseroCDRecord) stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
process (BraseroCDRecord) stdout: Drive buf size : 1267712 = 1238 KB
process (BraseroCDRecord) stdout: FIFO size      : 16777216 = 16384 KB
process (BraseroCDRecord) stdout: Track 01: data   682 MB        
process (BraseroCDRecord) stdout: Total size:      783 MB (77:39.72) = 349479 sectors
process (BraseroCDRecord) stdout: Lout start:      784 MB (77:41/54) = 349479 sectors
process (BraseroCDRecord) stdout: Current Secsize: 2048
process (BraseroCDRecord) stdout: ATIP info from disk:
process (BraseroCDRecord) stdout:   Indicated writing power: 4
process (BraseroCDRecord) stdout:   Is not unrestricted
process (BraseroCDRecord) stdout:   Is not erasable
process (BraseroCDRecord) stdout:   Disk sub type: Medium Type A, low Beta category (A-) (2)
process (BraseroCDRecord) stdout:   ATIP start of lead in:  -12508 (97:15/17)
process (BraseroCDRecord) stdout:   ATIP start of lead out: 359845 (79:59/70)
process (BraseroCDRecord) stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
process (BraseroCDRecord) stdout: Manuf. index: 22
process (BraseroCDRecord) stdout: Manufacturer: Ritek Co.
process (BraseroCDRecord) stdout: Blocks total: 359845 Blocks current: 359845 Blocks remaining: 10366
process (BraseroCDRecord) stdout: Starting to write CD/DVD at speed 32 in real SAO mode for single session.
process (BraseroCDRecord) stdout: Last chance to quit, starting real write in 3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
process (BraseroCDRecord) stdout: Waiting for reader process to fill input buffer ... input buffer ready.
process (BraseroCDRecord) stdout: BURN-Free is OFF.
process (BraseroCDRecord) stdout: Turning BURN-Free on
process (BraseroCDRecord) stdout: Performing OPC...
process (BraseroCDRecord) stdout: Sending CUE sheet...
process (BraseroCDRecord) set_action
process (BraseroCDRecord) stderr: cdrecord: CUE sheet not accepted. Retrying with minimum pregapsize = 1.
process (BraseroCDRecord) stderr: cdrecord: Success. send_cue_sheet: scsi sendcmd: no error
process (BraseroCDRecord) stderr: CDB:  5D 00 00 00 00 00 00 00 20 00
process (BraseroCDRecord) stderr: status: 0x2 (CHECK CONDITION)
process (BraseroCDRecord) stderr: Sense Bytes: 70 00 04 0E 93 20 20 0E 26 09 31 FE 08 01 00 00
process (BraseroCDRecord) stderr: Sense Key: 0x4 Hardware Error, Segment 0
process (BraseroCDRecord) stderr: Sense Code: 0x08 Qual 0x01 (logical unit communication time-out) Fru 0x0
process (BraseroCDRecord) stderr: Sense flags: Blk 244523040 (not valid) 
process (BraseroCDRecord) stderr: resid: 32
process (BraseroCDRecord) stderr: cmd finished after 2.215s timeout 200s
process (BraseroCDRecord) stderr: cdrecord: CUE sheet still not accepted. Please try to write in RAW (-raw96r) mode.
process (BraseroCDRecord) stderr: cdrecord: Cannot send CUE sheet.
process (BraseroCDRecord) stderr: cdrecord: Could not write Lead-in.
job (BraseroCDRecord) asked to stop
	status	= 1
	error		= 1
	message	= "the cd information could not be written"
iter (BraseroCDRecord) stopping
process (BraseroCDRecord) got killed
iter (BraseroCDRecord) stopped
job (BraseroCDRecord) got out of loop
job (BraseroCDRecord) set_task
Session error : the cd information could not be written






any ideas?
I'm really stumped and I need to get this workin.

---

### Post by wpshooter on 2006-12-20
Go into ADD/REMOVE programs and uninstall the K3b program.  Then reboot the machine, making sure your automatic sessions save button is marked.  And then go back into ADD/REMOVE program and reinstall the K3b program.

---

### Post by scxtt on 2006-12-20
don't use "sudo" for a GUI program, use gksu (gnome) or kdesu (KDE) to launch K3B:

#:> **kdesu k3b** ...

running it as root should help you rule out a permissions problem ... anytime i use k3b for the 1st time it has me alter the permissions for cd-recording (even tho ubuntu generally adds the 1st account to the "burning" group - or something like that) ...

---

### Post by Linux&amp;Lizards on 2006-12-21
how do I mark the automatick save buton?

---

### Post by jboss1995 on 2007-07-04
This is not a problem with k3b it is a problem with feisty not working with PIONEER DVD-RW DVR-110D. I have the same prob :(. It worked fine with 6.10 (Edgy Eft). Yes I did a fresh install of feisty and it has never worked consistently.

---

