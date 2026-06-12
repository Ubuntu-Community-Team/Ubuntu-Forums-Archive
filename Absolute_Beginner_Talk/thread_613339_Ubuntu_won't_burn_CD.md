---
title: "Ubuntu won't burn CD"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by LifeZagger on 2007-11-14
When I insert a blank disc, Ubuntu knows it is there and Nautilus can see it has a blank disc inserted.  I can't burn to that disc via CD/DVD Creator, Gnomebaker, Brasero or K3B.  I do have another drive that can successfully burn to dvds (that drive can't burn cds anymore even under windows).

I notice the following error in my sys logs:
Nov 14 20:28:08 ubuntu kernel: [ 4113.165272] hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }

I have no idea where to go from here!

Any help much appreciated.

---

### Post by Nano Geek on 2007-11-15
What happens when you try to burn it?

---

### Post by Inxsible on 2007-11-15
Are you sure its not a hardware problem?

If you dual boot, try to burn a disc with Windows and see if that works.

---

### Post by LifeZagger on 2007-11-15
> If you dual boot, try to burn a disc with Windows and see if that works. 

I can definitely burn cds in that drive with Windows XP.

I'm at work right now, but I'll try again later and make specific notes as to the error I am getting.  The basic gist of it was "Error: Can't write to disk".

I tried it in PCLinuxOS as well last night and has the same problem.  PCLOS knew I had a blank disk in there, but couldn't write to it.

Perhaps the specific drive isn't supported well in Linux?  I'm still pretty new to regular Linux use, so I don't know if that is a common issue.

---

### Post by twistedbydesign on 2007-11-15
If You have multiple CD drives make sure that you have the correct one selected on the program. I know when i tried burning CDs a few times it wasnt working because it was automatically set to the wrong CD drive. This may not be your problem...but it's a possibility. Start with the simplest things. lol. Good luck

---

### Post by DarthPooky on 2007-11-15
> **LifeZagger said:**
> I can definitely burn cds in that drive with Windows XP.

I'm at work right now, but I'll try again later and make specific notes as to the error I am getting.  The basic gist of it was "Error: Can't write to disk".

I tried it in PCLinuxOS as well last night and has the same problem.  PCLOS knew I had a blank disk in there, but couldn't write to it.

Perhaps the specific drive isn't supported well in Linux?  I'm still pretty new to regular Linux use, so I don't know if that is a common issue.

I have a samsung sw-240b that I salvaged from a dead emachine. Any ways it worked fine under windows 2k. then when I installed ubuntu 6.06 or 7.10 ubuntu would see the blank disc but when I tried to use the built in cd burner and it didn't see it then I installed k3b and no problem worked like a charm.=D>

---

### Post by LifeZagger on 2007-11-16
> **asjdfwejqrfjcvm msz34rq33 said:**
> What happens when you try to burn it?

In Gnomebaker it just says "failed", but I see this in the detail section:
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
resid: 64512
**************repeats a couple dozen times.....**************************
resid: 64512
TOC Type: 3 = CD-ROM XA mode 2
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'ATAPI   '
Identification : 'CD-RW 32/12/40X '
Revision       : '150C'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1806336 = 1764 KB
Drive DMA Speed: 53760 kB/s 305x CD 38x DVD
FIFO size      : 12582912 = 12288 KB
resid: 4
resid: 2
resid: 4
resid: 2
wodim: Warning: controller returns zero sized CD write parameter page.
wodim: Warning: controller returns wrong size for CD write parameter page.
wodim: Warning: controller returns wrong page 0 for CD write parameter page (5).
wodim: Warning: controller returns zero sized CD write parameter page.
wodim: Warning: controller returns wrong size for CD write parameter page.
wodim: Warning: controller returns wrong page 0 for CD write parameter page (5).
wodim: Cannot init drive.

---

