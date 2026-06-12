---
title: "burning problems"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by scrimple101 on 2008-01-20
Hi, i'm having trouble burning on my DVD drive which is a Pioneer dvd-rw dvd-112d. I have tried brasero and serpentine but they either take a long time and then say it failed or say that it has successfully burned but there is nothing on the disk. Is there some software that i need to install and/or configuration guides that might explain what the problem is? Regards, Rob

---

### Post by logos34 on 2008-01-20
you're trying to burn an audio cd?

---

### Post by scrimple101 on 2008-01-21
i'm trying to burn an iso of linux mint at the moment but i've tryed music before and it hasn't burnt.
regards, Rob

---

### Post by logos34 on 2008-01-21
try right-clicking on the mint .iso in nautilus file browser and choose 'write to disc'.  

Anything?

---

### Post by scrimple101 on 2008-01-21
it seems like it's burning and then it pops out and says: error writing to disk. try lower speed. I've tryed that before but it still doesn't work.

---

### Post by MegaJim on 2008-01-21
Bad disc/discs?

You could try using a rewritable cd and erasing it/burning stuff

---

### Post by logos34 on 2008-01-21
can you read cds and dvds, and play audio cds?

are you trying to burn cd-rw or cd-r?  all the same brand? (in other words, could it be faulty media?) it's happened to me trying to use ultra-speed 24x (memorex! never again)

---

### Post by scrimple101 on 2008-01-21
I think the media is OK because it burns in my wife"s cd burner. The drive works fine playing cds, dvds, and boots live dvds fine. Its just anything to do with burning things go wobbly. I'm using CD-R.

---

### Post by jken146 on 2008-01-21
It could be a lot of dust on the lens in your drive.

---

### Post by scrimple101 on 2008-01-21
i did clean the drive recently, and CDs and DVDs play fine. Are  CD-R OK for burning??

---

### Post by sailor2001 on 2008-01-21
I have had trouble with k3b but gnomebaker worked fine. try a different burning apt (synaptics)

---

### Post by scrimple101 on 2008-01-22
i downloaded gnomebaker and it failed to burn also - here is the output. Hope this means something to someone. Regards, Rob.

wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-112D'
Revision       : '1.09'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 705 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 4576
Writing  time: 1199.880s
Average write speed   4.0x.
Min drive buffer fill was 97%
Fixating...
Errno: 0 (Success), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 97 55 31 0E 00 00 00 00 72 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x72 Qual 0x00 (session fixation error) Fru 0x0
Sense flags: Blk 9917745 (not valid) 
cmd finished after 40.984s timeout 480s
cmd finished after 40.984s timeout 480s
Fixating time:   41.961s
wodim: Cannot fixate disk.
wodim: fifo had 11380 puts and 11380 gets.
wodim: fifo was 0 times empty and 11155 times full, min fill was 93%.

---

### Post by dysolve on 2008-01-22
i am having a similar problem with dvd's i have tried heaps of stuff and differant disc's and still no burn! driving me up the wall!

---

### Post by tgrisier on 2008-01-27
I too am having this problem.  I can read CD/DVD's just fine but can not burn.  I keep getting a 'can't write leadin' error.  I can burn just fine in Windows and could burn just fine under Feisty.

Any help would be much appreciated.

---

### Post by tgrisier on 2008-02-02
Bump, in the interest of getting this resolved.

---

### Post by bakermiller on 2008-02-04
I've had the same problem all day, i lost 2 disks. I finally got it working by going System >>  preferences >> removable drives and media >> and unselecting the "burn a cd when a blank disc is inserted" button. I get it must be a problem with the  way nautilus-cd-burner handles blank CD/DVDs, but i have no idea what i'm talking about. 

then i used Gnomebaker and it works fine at great speed.

---

