---
title: "dvdrecord warnings"
date: 2011-05-12
forum: Any Other OS
---

### Post by qyot27 on 2011-05-12
Currently the only adequately-working DVD burner in this house is in the iMac, so I've gotten used to burning discs with OSX's built-in Disk Utility software.  It's not the most elegant way (as in: it requires a bunch of extra clicking and closing of Finder windows that IMO shouldn't be getting opened in the first place), but at least it works.


A bit more background, because this will explain some further reasoning here:
When I construct the ISO images, I frequently had to do a couple of things to get them over to the iMac.  Before getting a 16GB flash drive for Christmas a few months ago, I packed the image in spanned 7z archives, transported it over on a couple of smaller 4GB drives, unpacked, and then used the Disk Utility to burn.

Since I have a 16GB drive now, I write the image directly to that drive first and forgo the whole spanned archive thing.  However, this resulted in me running headfirst into FAT's filesize limit.  Luckily, the program I was using (ImgBurn) could split the file automatically and use its reference file to use the two parts seamlessly.

Problem is, Disk Utility doesn't understand this reference file, making the two parts useless for accurate burning.  Turns out, however, that a simple *cat* will restore the image to its original state.  Furthermore, the split parts on the drive can still verify against a disk that OSX burnt using the *cat*-joined image.

So basically, I build the ISO image with ImgBurn, directing to the flash drive.  It's automatically split into two pieces because of FAT's filesize limitations.  I copy the two halves to the iMac's hard drive and then use *cat* (often in a shell script, especially useful when I have multiple discs I need to burn) to rejoin them.




My problem, is that I have a bad habit of forgetting to check on the rejoining process, wasting time that could have been getting used to burn the disc.  After suffering through this many times over the last few months, I started thinking about letting the burn process automate with the rejoin operation.  So I installed dvdrecord from MacPorts, and after a bit of research, managed to burn a disc successfully.  It verified successfully in ImgBurn as well.

I still have questions regarding this, though.


Is dvdrecord recommended over the normal cdrecord from cdrtools?  I know the latter can burn DVDs, but is there any reason to pick one over the other?  dvdrecord is a branch of cdrecord, but I don't know if it's got necessary advantages or is still being updated, etc.

EDIT: Yeah, seems like the 'outdated' part was right - dvdrtools hasn't been updated in years, and the port for cdrtools is for 3.00.  I'll have to try again with cdrtools next time I need to burn something, and see if the warnings persist.

As per the thread title, I did get a warning concerning setpriority().  I would *guess* that it means I should use sudo to run dvdrecord instead of running it as a normal user, even though the burn went fine as a normal user (it warning about the possibility of buffer underruns is what's scaring me).  The log is posted below:

> $ ./audio.sh
+ cat Misc-5.12.11.i00 Misc-5.12.11.i01
+ cat Misc-5.12.11-2.i00 Misc-5.12.11-2.i01
+ dvdrecord -v -dao speed=4 dev=IODVDServices -eject -v Misc-5.12.11.iso
dvdrtools v0.2.1
Portions (C) 2002-2005 Ark Linux <bero@arklinux.org>
This program is free software; you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free Software
Foundation; either version 2, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR
A PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with
this program; see the file COPYING.  If not, write to the Free Software
Foundation, 59 Temple Place, Suite 330, Boston, MA 02111-1307, USA.
Based on:
Cdrecord 1.11a15 (i686-apple-darwin10.7.0) Copyright (C) 1995-2001 J?rg Schilling
TOC Type: 1 = CD-ROM
dvdrecord: Function not implemented. WARNING: Cannot do mlockall(2).
dvdrecord: WARNING: This causes a high risk for buffer underruns.
dvdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
dvdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: 'IODVDServices'
devname: 'IODVDServices'
scsibus: -2 target: -2 lun: -2
Using libscg version 'bero-0.5a'
dvdrecord: Warning: using inofficial version of libscg (bero-0.5a '@(#)scsitransp.c	1.81 01/04/20 Copyright 1988,1995,2000 J. Schilling').
Using libscg transport code version 'csapuntz-scsi-mac-iokit.c-1.3'
dvdrecord: Warning: using inofficial libscg transport code version (csapuntz-scsi-mac-iokit.c-1.3 '@(#)scsi-mac-iokit.c	1.3 01/10/29 Copyright 1997,2001 J. Schilling').
atapi: 0
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identifikation : 'DVD-R   UJ-85J  '
Revision       : 'FCQ5'
Device seems to be: Generic mmc2 DVD.
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1605632 = 1568 KB
FIFO size      : 4194304 = 4096 KB
Track 01: data  4402 MB        
track: 1 start: 0 pregap: 150
Total size:     5055 MB (500:53.12) = 2253984 sectors
Lout start:     5056 MB (500:55/09) = 2253984 sectors
 41 00 00 14 00 00 00 00
 41 01 00 10 00 00 00 00
 41 01 01 10 00 00 02 00
 41 AA 01 14 00 F4 37 09
Track 1 start 0
Track 2 start 2253984
 41 00 A0 00 00 00 00 01 00 00 00 00
 41 00 A1 00 00 00 00 01 00 00 00 00
 41 00 A2 00 00 00 00 FE 55 09 00 00
 41 00 01 00 00 00 00 00 02 00 00 00
Current Secsize: 2048
  ATIP start of lead in:  -150 (00:00/00)
Disk type:    unknown dye (reserved id code)
Manuf. index: -1
Manufacturer: unknown (not in table)
Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 44512
dvdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
dvdrecord: WARNING: This causes a high risk for buffer underruns.
Starting to write CD/DVD at speed 4 in write mode for single session.
Last chance to quit, starting real write in 0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
trackno=0
BURN-Free is ON.
Performing OPC...
Sending CUE sheet...
dvdrecord: WARNING: Drive returns wrong startsec (0) using -150
Starting new track at sector: 0
Track 01: 4402 of 4402 MB written (fifo 100%).
Track 01: Total bytes read/written: 4616159232/4616159232 (2253984 sectors).
Writing  time:  901.729s
Fixating...
Fixating time:   71.190s
dvdrecord: fifo had 140874 puts and 140874 gets.
dvdrecord: fifo was 0 times empty and 40395 times full, min fill was 69%.
+ read -n1 -r -p 'Press any key to continue...' key
Press any key to continue...

The particular warnings are these:
> dvdrecord: Function not implemented. WARNING: Cannot do mlockall(2).
dvdrecord: WARNING: This causes a high risk for buffer underruns.
dvdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
dvdrecord: WARNING: This causes a high risk for buffer underruns.

...

Using libscg version 'bero-0.5a'
dvdrecord: Warning: using inofficial version of libscg (bero-0.5a '@(#)scsitransp.c	1.81 01/04/20 Copyright 1988,1995,2000 J. Schilling').
Using libscg transport code version 'csapuntz-scsi-mac-iokit.c-1.3'
dvdrecord: Warning: using inofficial libscg transport code version (csapuntz-scsi-mac-iokit.c-1.3 '@(#)scsi-mac-iokit.c	1.3 01/10/29 Copyright 1997,2001 J. Schilling').

...

dvdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
dvdrecord: WARNING: This causes a high risk for buffer underruns.

...

dvdrecord: WARNING: Drive returns wrong startsec (0) using -150

---

### Post by qyot27 on 2011-05-13
Marking the thread as solved because of this:

> Yeah, seems like the 'outdated' part was right - dvdrtools hasn't been updated in years, and the port for cdrtools is for 3.00.  I'll have to try again with cdrtools next time I need to burn something, and see if the warnings persist.

---

