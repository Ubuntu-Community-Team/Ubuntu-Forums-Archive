---
title: "CD/DVD Burning Help!!! (Commandline Options?"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-02-08
**Edit: Hit enter while typing my mistake**

Ok so I'm running Ubuntu Edgy with Xfce (xubuntu I guess). And I've been having some real problems burning CD's

I've tryed xfburn, and k3b and I keep getting an error when trying to burn a file or copy a cd. Something about my kernel version and about cdrecord or something not been supported or modified. I do not want to waste another CD to do it again to find the error message.

So I was wondering if anyone new why this could be happening and how to fix it.

On another note, to avoid a GUI program I would not mind using the command line to burn CD's. The commands I would need to know is how to burn a file to a CD/DVD, how to copy a CD/DVD (including Data, Audio, DVD, etc), and how to burn a audio CD from flac,mp3,ogg files etc.

Anyhelp would be awesome.

---

### Post by ahaslam on 2007-02-08
Those are generic warnings that we all get, but if it's not working your permissions probably need changing.

The usuall fix is: *sudo chmod +s /usr/bin/cdrecord*

If you're still getting problems, either launch the app through the cli & post any output, or try with cdrecord directly: *sudo cdrecord -dev ATAPI:/dev/hdc -data /path/to/file*

Tony.

---

### Post by ahaslam on 2007-02-08
Useful links:

[http://linuxreviews.org/howtos/cdrecording](http://linuxreviews.org/howtos/cdrecording)
[http://gentoo-wiki.com/HOWTO_Create_a_DVD:Burn](http://gentoo-wiki.com/HOWTO_Create_a_DVD:Burn)
[http://www.debuntu.org/2006/06/03/61-how-to-burn-dvds-from-the-command-line](http://www.debuntu.org/2006/06/03/61-how-to-burn-dvds-from-the-command-line)

;)

---

### Post by guysmiley25 on 2007-02-08
Here we go

```

# sudo cdrecord -dev ATAPI:/dev/scd0 -data "~/file of movie.avi"

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.17-10-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: 'ATAPI:/dev/scd0'
devname: 'ATAPI:/dev/scd0'
scsibus: -2 target: -2 lun: -2
Warning: Using ATA Packet interface.
Warning: The related Linux kernel interface code seems to be unmaintained.
Warning: There is absolutely NO DMA, operations thus are slow.
cdrecord: ERROR: unknow subsystem (scd0) in (/dev/scd0)
cdrecord: Success. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord: 
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

```

---

### Post by tbroderick on 2007-02-08
Your burner is at /dev/scd0? Then try;
```

sudo cdrecord dev=/dev/scd0 

```

It should be cdrecord dev=xxx not -dev xxx.

---

### Post by guysmiley25 on 2007-02-08
Ok so here is wher I'm at:

```

guysmiley@guysmiley:/$ sudo cdrecord dev=/dev/scd0 -data "/file of movie.avi"
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.17-10-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Error trying to open /dev/scd0 exclusively (Device or resource busy)... retrying in 1 second.
Linux sg driver version: 3.5.27
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : '_NEC    '
Identifikation : 'DVD_RW ND-3500AG'
Revision       : '2.16'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Starting to write CD/DVD at speed 32 in real TAO mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 04 10 00 00 10 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 32768
cmd finished after 0.010s timeout 40s
write track data: error after 2129920 bytes
cdrecord: The current problem looks like a buffer underrun.
cdrecord: Try to use 'driveropts=burnfree'.
cdrecord: Make sure that you are root, enable DMA and check your HW/OS set up.

```

And I've made a few coaters!

Any help will be really awesome!

---

### Post by ahaslam on 2007-02-08
OK, I did not realise that you were burning files, my method only works with iso images (I probably confused things further by saying* '/path/to/file'* - sorry). You'll need to create an iso image with mkisofs first, it's quite simple. To save typing, this is from [here]("http://freeunix.dyndns.org:8088/site2/howto/Burn_em_Baby.shtml"):
> 
When you want to create a data cd, you will need to make an ISO filesystem before you can burn the file to a cd-r(rw). This process, the premastering, is done with mkisofs. Needless to say you have to make sure you have enough free diskspace available to store both the image tree and the image itself (so, you'll need at least 2x the space).

mkisofs produces an ISO 9660 file system that is an image of a directory tree in a Linux/Unix file system. The simplest usage is:

 # mkisofs -r -o imagefile.iso /path/to/tree 

The "-r" option sets the permissions of all files and dirs to be public readable and enables the RockRidge extensions (allowing long filenames). This command will thus create a file called imagefile.iso containing an ISO 9660 file system with RockRidge extensions that is a copy of the tree at /path/to/tree.
You can then burn the imagefile as shown above. If you want to test the file to check the layout, you can mount it first, like this :

 # mount -t iso9660 -o ro,loop=/dev/loop0 /mnt/cdrom

You can then inspect the files by cd'ing to /mnt/cdrom. To unmount, just issue unmount /mnt/cdrom/. Your Linux kernel needs support for so-called "loopback" devices to be able to mount an ISO image like this. 

OK, you should have an iso image ready to burn. Your previous attempt suggested, *Try to use 'driveropts=burnfree'.* So my suggestion is as follows:

```
[SIZE="3"]sudo cdrecord dev=/dev/scd0 driveropts=burnfree -data /your/new/**.iso**[/SIZE]
```

Tony.

PS, Experiment with a CD-RW - you don't want a house full of shiny coasters ;)

---

### Post by tbroderick on 2007-02-08
> **guysmiley25 said:**
> Ok so here is wher I'm at:

```

cdrecord: The current problem looks like a buffer underrun.
cdrecord: Try to use 'driveropts=burnfree'.
cdrecord: Make sure that you are root, enable DMA and check your HW/OS set up.

```

And I've made a few coaters!

Any help will be really awesome!

Every burner is a little different. You might be burning at too high a speed. I'd  suggest trying the 'driveropts=burnfree' option and -verbose (or just -v for short) to get more verbose messages. You could also try setting the speed with speed=12 or whatever. Last, try different burn mode like -sao.

```

sudo cdrecord dev=/dev/scd0 -v driveropts=burnfree -data "/file of movie.avi"

```

It's too bad you don't have an RW to erase any bad burns (sudo cdrecord dev=/dev/scd0 -v blank=fast).

---

### Post by ahaslam on 2007-02-08
> **tbroderick said:**
> Your burner is at /dev/scd0? Then try;
```

sudo cdrecord dev=/dev/scd0 

```

It should be cdrecord dev=xxx not -dev xxx.

I need the [SIZE="5"]**[COLOR="Red"]-[/COLOR]**[/SIZE] strange eh?

---

### Post by tbroderick on 2007-02-08
> **Anthony Haslam said:**
> I need the [SIZE="5"]**[COLOR="Red"]-[/COLOR]**[/SIZE] strange eh?

Yeah. I've only had 2 different burners and dev= as always worked for me.

---

### Post by guysmiley25 on 2007-02-09
Ah!!!! here is where I'm at:

```

guysmiley@guysmiley:/$ sudo cdrecord dev=/dev/scd0 driveropts=burnfree -data /movie.iso
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.17-10-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : '_NEC    '
Identifikation : 'DVD_RW ND-3500AG'
Revision       : '2.16'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Starting to write CD/DVD at speed 32 in real TAO mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 32 90 00 00 10 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 2F EA 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 12266 (not valid) 
resid: 32768
cmd finished after 23.440s timeout 40s
write track data: error after 26509312 bytes
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.
cdrecord: Input/output error. close track/session: scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 72 04 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x72 Qual 0x04 (empty or partially written reserved track) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.005s timeout 480s
cmd finished after 0.005s timeout 480s
cdrecord: Cannot fixate disk.

```

Also if it helps anyone help me!

```

guysmiley@guysmiley:/$ cdrecord -scanbus
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.17-10-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
Linux sg driver version: 3.5.33
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus4:
        4,0,0   400) '_NEC    ' 'DVD_RW ND-3500AG' '2.16' Removable CD-ROM
        4,1,0   401) *
        4,2,0   402) *
        4,3,0   403) *
        4,4,0   404) *
        4,5,0   405) *
        4,6,0   406) *
        4,7,0   407) *

```

I'm going to do a reinstall, just because I feel like it so maybe this will help. The CD/DVD Writer is an external USB one also.

Thanks for all the help so far guys!

---

### Post by ahaslam on 2007-02-09
Did you also try: **sudo cdrecord -v dev=4,0,0 driveropts=burnfree -data /path/to/.iso**

This, like my previous suggestions, will burn at full speed. You may wish to consider a more conservative setting with 'speed=*whatever*' as previously suggested by tbroderick. More info on this & other options can be found within the links I posted.

Tony.

PS. Was that a fresh/blanked disc you tried? A similar error appears when attempting a burn on a cd-rw without prior blanking :-k

PPS. '***[COLOR="Red"]/[/COLOR]**movie.iso*' - is that right :-k

---

### Post by guysmiley25 on 2007-02-12
Ok so I've giving up on that computer for a while, and used my laptop as I needed to get the job done!

But how would I go about copying a audio cd? I want to use a commandline, and I would like to know how to copy to a cue/bin or cue/wav or whatever and how to do a straight copy.

Thanks.

---

### Post by guysmiley25 on 2007-04-19
Ok how about copying an audio cd to cd in the commandline?

---

