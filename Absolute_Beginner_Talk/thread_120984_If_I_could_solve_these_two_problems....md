---
title: "If I could solve these two problems..."
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by Cysman on 2006-01-24
I'm a brand new linux user pretty much but this whole Ubuntu thing has me pretty stoked.  I'd be a real happy muchacho if I could do two things:

1. Burn a cd
2. Convert m4a to mp3.

I've tried Kb3 and Gnomebaker to burn cd's and nothing seems to work.  I've checked my name on the user list and it's check for me to use it but when I check the properties of my cdrw it tells me I'm not the owner and can't change permissions.:confused: 

I have successfully installed pymusique and bought my first song but it is downloaded in m4a.  I don't have an Ipod and need to convert this to mp3.  Any suggestions?

---

### Post by ardchoille on 2006-01-24
[QUOTE=Cysman]I'm a brand new linux user pretty much but this whole Ubuntu thing has me pretty stoked.  I'd be a real happy muchacho if I could do two things:

1. Burn a cd
2. Convert m4a to mp3.

I've tried Kb3 and Gnomebaker to burn cd's and nothing seems to work.  I've checked my name on the user list and it's check for me to use it but when I check the properties of my cdrw it tells me I'm not the owner and can't change permissions.:confused: 

I have successfully installed pymusique and bought my first song but it is downloaded in m4a.  I don't have an Ipod and need to convert this to mp3.  Any suggestions?[/QUOTE]

1. Install and use graveman. It's a nice CD burning app and it's in the universe repo.

---

### Post by kokiri on 2006-01-24
Instructions on how to convert m4a to mp3 can be found [here.]("http://www.togaware.com/linux/survivor/m4a_mp3.shtml")

You will need to enable universe repositories to be able to install faad and lame. After that just follow the instructions on the above site.

---

### Post by Cysman on 2006-01-24
Well, I tried that and when it came to burning the cd, this is what I got: 

Can't open input file '(null)': No such file or directory

Man oh man oh man..............

---

### Post by Cysman on 2006-01-24
I'm not very familiar with the command line thing.  But somewhere in the command, is there a place where I should be putting in the name of the actual file I want to convert?

---

### Post by Cysman on 2006-01-24
This is also what I get when I use Gnomebaker:



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

TOC Type: 1 = CD-ROM
Using libscg version 'ubuntu-0.8ubuntu1'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'PHILIPS '
Identifikation : 'CDD4851 CD-R/RW '
Revision       : 'C3.7'
Device seems to be: Generic mmc CD-RW.
Current: 0x000A
Profile: 0x0008 
Profile: 0x0009 
Profile: 0x000A 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET RAW/R16 RAW/R96R
Drive buf size : 3244032 = 3168 KB
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Reference speed: 2
  Is not unrestricted
  Is erasable
  ATIP start of lead in:  -11635 (97:26/65)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low:  0 (reserved val  0) 1T speed high:  4
  2T speed low:  8 2T speed high:  0 (reserved val 10)
  power mult factor: 4 6
  recommended erase/write power: 3
  A1 values: 02 4C B0
  A2 values: 4A C8 36
Disk type:    Phase change
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Starting to write CD/DVD at speed 4 in real BLANK mode for single session.
Last chance to quit, starting real write in 5 seconds.   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Performing OPC...
cdrecord: OPC failed.
Blanking entire disk
cdrecord: Success. blank unit: scsi sendcmd: no error
CDB:  A1 00 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 13 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 1.907s timeout 9600s
cdrecord: Cannot blank disk, aborting.
Ah fiddlestix

That last part I put in myself

---

### Post by kokiri on 2006-01-24
yes. 
for simplicity sake I would create a directory in your home folder called "convert"  (without the quotes of course)
Then I'd use the file manager and move or copy the m4a files that I wanted to convert into the newly created directory
Then I'd open a terminal window and type:
cd convert  (enter)
the prompt should look something like this  blah@blah:~convert/$
you can type "ls" to see what's in the directory just to verify that your m4a files you want to convert are there
lets say there's a song there named "test.m4a" substitute the test.m4a name for one of your real file names
So going by the example I would then type:
faad -o test.wav test.m4a
what this will do is make a wave file out of the original m4a file. The -o stands for "output the file on the end of this command into wave format with the name immediately behind -o"

---I can go more ad-nauseum if you need but the rest of the page pretty much lets ya know how to use the programs for this purpose

---

### Post by Limulus on 2006-01-24
[QUOTE=Cysman]when I check the properties of my cdrw it tells me I'm not the owner and can't change permissions.:confused:[/QUOTE]
Huh.  Try this:

Go System -> Administration -> Users and Groups

in the user list, click your username (even if its the only one ;)

click the Properties button

a Settings window will open; click the User privileges tab

is there a checkmark next to Use CD-ROM drives?  If not, add it :)

---

### Post by Cysman on 2006-01-24
Yes, there is.  Actually, it has been checked from the start.

---

### Post by Cysman on 2006-01-24
Ok, I did what you suggested and all went fine untill.....

this:

kenoutten@ubuntubedroom:~$ cd convert
kenoutten@ubuntubedroom:~/convert$ faad -o Dont Lie.wav Dont Lie.m4a
 *********** Ahead Software MPEG-4 AAC Decoder V2.0 ******************

 Build: Oct  9 2005
 Copyright 2002-2004: Ahead Software AG
 [http://www.audiocoding.com](http://www.audiocoding.com)
 Floating point version

 This program is free software; you can redistribute it and/or modify
 it under the terms of the GNU General Public License.

 **************************************************************************

Error opening file: Lie.wav
kenoutten@ubuntubedroom:~/convert$

I must still be doing something wrong.

---

### Post by Tiede on 2006-01-24
in the command line, spaces are interpreted differently than in the graphical user interface. In your commands, if ever there is a space somewhere,always replace with a backslash followed by the space. For example, "I love the command line" would be wirtten like so: I\ love\ the\ command\ line. Notice also that putting the filename in quotes also work just fine.

---

### Post by Cysman on 2006-01-24
Wow, with your help and me dinking around with the instructions, It worked!  I've actually got a smile on my face.  Thanks alot for the help

Ken

---

### Post by Tiede on 2006-01-24
Always a pleasure to help out. This community has done so much for me, it would be difficult for me to think of doing otherwise. ;)

---

### Post by jimrz on 2006-01-24
Looks like problem with the file name. Try renaming it to get rid of the space [and probably the ' as well]in the file name, like maybe DontLie.xxx or Dont_Lie.xxx

---

### Post by Cysman on 2006-01-25
It ended up working by putting quotes around the file name i.e. "Dont Lie.wav".  Thanks though.

---

### Post by Limulus on 2006-01-25
[QUOTE=Cysman]I've tried Kb3 and Gnomebaker to burn cd's and nothing seems to work.  I've checked my name on the user list and it's check for me to use it but when I check the properties of my cdrw it tells me I'm not the owner and can't change permissions.:confused:[/QUOTE]

When you put in a CDRW, what happens?  Does it mount it?

Try running *sudo nautilus* (that is, the file explorer using root permissions via sudo) and then navigate to the CD drive to look at/try to alter the permissions...

BTW, just to rule it out, you installed K3B via the normal way? (apt/synaptic)

---

### Post by Cysman on 2006-01-25
When I put in the cdrw it mounts and puts it into the desktop.  Then, a window pops up and asks me what I want to do, including burning a cd.  I installed K3B via the add program option on the drop down menu.

---

### Post by bikeboy on 2006-01-25
Another quick tip on using the command line is that "Tab" is your friend. When you're not sure how to type a filename, type the 1st few letters then hit Tab. It will autocomplete based on the files in your current directory.
eg. $cp Don (then hit tab)
      $cp Don't\ Lie.wav (will appear)

If there is more than 1 possible completion you can type a little further, or press Tab again and it will show you the possibilities.

Helps in situations like you had, and with any long commands as well.

---

