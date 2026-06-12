---
title: "Cannot Burn CD\DVD"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by pdiki on 2007-02-21
Hi,

First of all, im loving ubuntu, ive just switched from XP and am already wondering why it has taken me so long!

My only issue so far is that i cant burn Cd's or DVD's, ive insatlled various different applications (such as GnomeBaker, k3B) to try and burn both audio CDs and DVDs with no success, which leads me to believe that i have a problem with my burner. 

Hence the problem, i have no idea to work out what is wrong with and what i need to do to fix it!?

My burner is a Pioneer 106D. and it worked perfectly fine in XP. Ive already done a lot of searching on the problem both in the forum and in google and tried a lot of things but to no avail :(

Any help would be very appreciated. 
Thanks in advance,
Paul

---

### Post by rbprogrammer on 2007-02-21
i have problems with my phillips cd/dvd burner with k3b when i run the program as a user.... the only way i can get around that problem is run the program as [sudo].

for your situation, i would suggest that you pick a program that you think you will like, and post some error messages from the program.  it seems like your problem is just too broad or vague right now.

---

### Post by pdiki on 2007-02-21
Thanks for the fast response!!

For example i have an iso that i want to burn to disc. In the file browser if i right click on it and click Write to Disc... I get a window that allows me to set some options (see attached Screenshot -Write to disc), it also finds my burner. I click write then after about 20 secs i get a Error writing to disc message (see attached error). This happens no matter what program i use.

Thanks

---

### Post by rbprogrammer on 2007-02-21
does the drive start to spin or make any noises before it has that fatal error?

i've only been using ubuntu for about a year, but i still consider myself a noobie... i would try to burn the iso image using [sudo].  you may even login as root, but that is supposed to be ***dnagerous***.  nothing has ever happened to me when i do a root login, but i think it still has the potential to do damage if you dont know what you are doing.

---

### Post by pdiki on 2007-02-21
Hi 

I just tried using  sudo growisofs -dvd-compat -Z /dev/hdc=/home/paul/casino_royale.iso

And got the following:

Executing 'builtin_dd if=/home/paul/casino_royale.iso of=/dev/hdc obs=32k seek=0'
:-[ PERFORM OPC failed with SK=4h/ASC=44h/ACQ=D9h]: Input/output error
/dev/hdc: "Current Write Speed" is 4.1x1385KBps.
:-[ WRITE@LBA=310h failed with SK=4h/ASC=44h/ACQ=D9h]: Input/output error
:-( write failed: Input/output error
/dev/hdc: flushing cache
/dev/hdc: updating RMA
/dev/hdc: closing disc

Does this make any sense to anyone? lol

Cheers,
Paul

---

### Post by peter.faller on 2007-04-26
Similar problems with a BEN-Q DVD+RW drive - the only solution I have found is to mount the drive in an external USB case and use my Windows laptop (:-P) to burn discs. That works without problems.

---

### Post by claesbrandt on 2007-07-26
I don't know if this helps. I couldn't burn DVDs either (I could however burn CDs). I tried to enable DMA for my drive using the command sudo hdparm -d1 /dev/<devicename> but hdparm fails doing this. I instead tried to burn at a slower speed. I can see you have tried at 4x. Try at 2x. That works for me.

---

### Post by chepeadan on 2007-08-16
hello i had the same problem burning cds and dvds...
what i dicovered is that ubuntu has problems with some cd brands..like memorex and sometimes sony...i couldnt write cds in ubuntu with thouse brands...but TDK cds worked like a charm....
why dont u guys buy one tdk cd ...and try it..please dont buy 50 i dont make myself responsable if it doesnt work for u  :lolflag:
i will apreciate any comment...

---

### Post by daradib on 2007-08-21
I can't burn CDs (TDK) on a Dell Computer (with PHILIPS DVD+-RW DVD8801).

I tried both wodim and cdrskin in K3B, but both fail.
Both fail Optimum Power Calibration. Cdrskin continues after OPC fails because of a --force option, but then fails while writing the lead-in (I think).

When using wodim:
```
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 12 00 00 00 00 09 00 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x09 Qual 0x00 (track following error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 7.718s timeout 200s
/usr/bin/wodim: OPC failed.
Writing  time:   11.810s
```

When using cdrskin:
```
Executing power calibration...
ERROR: Power calibration failed.
ERROR: Ignored because of option --force.
/usr/bin/cdrdao: Input/output error.  : scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1A 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 12 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 61152
cmd finished after 11.304s timeout 180s
ERROR: Write data failed.
ERROR: Writing failed.
```

Similar problems with GnomeBaker and Serpentine.

---

### Post by daradib on 2007-08-22
Here are the entire debug texts.

---

### Post by daradib on 2007-08-22
Problem appears to be hardware related (CDs or burner) since I can't burn in Windows either.

---

### Post by likemindead on 2007-08-23
Yeah... here's what I got just a minute ago the first time I tried to burn a CD:

```
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'MITSUMI '
Identification : 'CR-48X9TE       '
Revision       : '5.0E'
Device seems to be: Philips CDD-522.
Current: 0x0009 (CD-R)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
Drive buf size : 1589248 = 1552 KB
FIFO size      : 12582912 = 12288 KB
dSpeed set to 4234 KB/s
 writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 158978
Starting to write CD/DVD at speed  24.0 in real TAO mode for single session.
Last chance to quit, starting real write in 5 seconds.   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 16.992s timeout 60s
wodim: OPC failed.
Writing  time:   18.501s

```

I don't even know where to begin. Help? And *big* thanks in advance....

---

### Post by sancelot on 2007-08-24
> **pdiki said:**
> Hi 

I just tried using  sudo growisofs -dvd-compat -Z /dev/hdc=/home/paul/casino_royale.iso

And got the following:

Executing 'builtin_dd if=/home/paul/casino_royale.iso of=/dev/hdc obs=32k seek=0'
:-[ PERFORM OPC failed with SK=4h/ASC=44h/ACQ=D9h]: Input/output error
/dev/hdc: "Current Write Speed" is 4.1x1385KBps.
:-[ WRITE@LBA=310h failed with SK=4h/ASC=44h/ACQ=D9h]: Input/output error
:-( write failed: Input/output error
/dev/hdc: flushing cache
/dev/hdc: updating RMA
/dev/hdc: closing disc

Does this make any sense to anyone? lol

Cheers,
Paul


Are you sure you have to use /dev/hdc it is not /dev/scd0 ?

---

### Post by suprughetto on 2007-10-02
I jump in this old post because I have the same problem with my DVD rewritable  Philips 1668P1. Did you find the solution?

---

### Post by Johnny3 on 2007-10-02
At first my cd/dvd would stop in the middle of burn and open cd/dvd player. Forum told me how to turn off auto-play. System/Preferences/Removable Drives and Media. On the storage tap only check the top two. The ones that say mount and it stopped doing that. Mite be worth a try.
Thanks Johnny3
Gainesville, Fl

---

### Post by RobsterUK on 2007-10-23
I'm also suffering the same problem and have been for some time, since I upgraded when 7.04 came out (had no problems with it in 6.10)

Error output below
```
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '1,1,0'
scsibus: 1 target: 1 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TOSHIBA '
Identification : 'DVD-ROM SD-R1002'
Revision       : '1038'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009 (CD-R)
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R
Drive buf size : 1312768 = 1282 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 706 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 14 00 00 00 00 0E 09 0C 00 50 00 03 00 00
Sense Key: 0x4 Hardware Error, Segment 11
Sense Code: 0x00 Qual 0x03 (setmark detected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.497s timeout 60s
wodim: OPC failed.
Writing  time:    5.077s

```

It would be annoying if this problem was fixed in 7.10 as that's what I'm currently trying to burn.

---

### Post by olebaillif on 2007-10-31
Have the same problem here.  I have been fighting with the gnomebaker and other gui tools for a while and finally decided to use CDRDAO and see for myself...

Here is the ouput when comes time to write the image onto the disk:

root@Aldair:~# cdrdao write --device ATAPI:1,0,0 cd29936.toc
Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.

Using libscg version 'ubuntu-0.8ubuntu1'

ATAPI:1,0,0: Memorex DVD16+/-DL4RWlD2   Rev: JWS5
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0000)

Starting write at speed 48...
Pausing 10 seconds - hit CTRL-C to abort.
Process can be aborted with QUIT signal (usually CTRL-\).
Turning BURN-Proof on
Enabling JustSpeed.
Executing power calibration...
Power calibration successful.
cdrdao: Input/output error.  : scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1A 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 64 00 00 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x64 Qual 0x00 (illegal mode for this track) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 180s
ERROR: Write data failed.
ERROR: Writing failed.


This looks very familiar to quite a few errors that I have seen googling around.  the error code migth be different but overall quite a few people get in trouble right at the sensing part.

Did not have a problem burning CDs before I went to Gutsy 7.10.  Can't remember if I burned a CD in feisty but I know I sure did burn CDs and DVDs when I ran opensuse 10.2 (just recently switched to ubuntu)

Any recommendations? or suggestions to try to debug this further? 

Thanks

---

### Post by mateuszbaranski on 2007-10-31
Have the same problem in Kubuntu 7.04.
common problem with k3b (wodim program) "OFC failed" 
It llooks that I have problem mostly with CDRW (CDR is OK)


Mateusz

---

### Post by Pumalite on 2007-10-31
Beyond hardware failure (clean the lens, replace burner), you guys should do two things: go to /dev and check if you have a cdrom device to make sure your kernel is loading the module. If it's not there, go to BIOS and set burner either to AHCI or 2nd Master and 'Auto'

---

### Post by olebaillif on 2007-11-01
Yes I do have a cdrom device in /dev and it works perfectly fine when I read CD/DVDs I can rip anything I want but not write it back to a blank one.  Whether it is a CD or DVD.  Same blanks used to work a few month back in openSuse.

---

### Post by Pumalite on 2007-11-02
It might be that the time came to change your burner.

---

### Post by linette on 2008-03-21
I also seem to be having a similar problem.

I have a Pioneer DVD-RW internal drive, mounted in an external case connected by USB.

The Drive works fine under windows.

When I try and use it in Gutsy, it will spin, stop. spin. stop for a few times, as if the media is incorrect or the drive is faulty.  Sometimes it will eventually spin up correctly.  Other times not.  I've had very limited success burning (seems CD will work occasionally, but not DVDs) and if it fails then the device 'goes missing' from the system.  It is no longer listed as an option in K3b for example.

If it wasn't for the fact that it works fine when connected to windows systems, I would have diagnosed it as a faulty drive.

Any ideas?  Whilst I can do tech support in Windows, as a noob to linux I'm flailing a bit here!

Halp!

---

### Post by caprian81 on 2008-05-07
> **likemindead said:**
> Yeah... here's what I got just a minute ago the first time I tried to burn a CD:

```
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.

```

----


Has anyone set CDR_NODMATEST environment variable?  Might that work?

---

