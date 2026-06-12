---
title: "Help mounting the dvd/cd drive?"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by staib on 2007-12-23
Laptop - Lenovo 3000 N200 - Vista and 7.10 dual booting

Trying to see contents of a data DVD but error message says "mount: special device /dev/scd0 does not exist".   

Please can someone tell me how to make it exist?!

Thanks.

---

### Post by blueridgedog on 2007-12-23
For the sake separating the problem, can you put another disk in, one that you have accessed with Ubuntu before?  I want to know if we should look at the disk or the drive.

---

### Post by staib on 2007-12-24
There was I thinking it was an ubuntu software thing.  But I just tried Vista and that can't see the dvd/cd re-writer either - I don't really know Vista too well, but assumed the drive would be visible along with the 'C drive' in the 'Computer view'...    

Odd - as it was all working fine a few weeks ago - I had tried a DVD film (Apocalypse Now - what else?!) in Vista and that was fine - and I obviously installed Ubuntu a few weeks back, so that was good.  

Both Ubuntu and Vista recognise a USB drive immediately...  I will next try and see if the laptop will even boot from the 7.10 disc...

---

### Post by blueridgedog on 2007-12-24
Sorry to hear, however, I do find it fascinating that at the point in which something breaks, we immediately think "well, it was working before".  Did you try another disk just to be certain?

Good luck.

---

### Post by philinux on 2007-12-24
> **staib said:**
>  I will next try and see if the laptop will even boot from the 7.10 disc...

That sounds a good idea since this was your install disc I presume? No DRM to cloud the issue.

---

### Post by staib on 2007-12-24
OK - just tried booting from the install/live disk and that loaded fine. This suggests there is  not a 'physical' problem with the drive.

I went into Places > Computer and could see the the icon for CD-ROM 1.  However I got a similar message trying to open the CD to read its contents - I think the exact error message suggested there was no CD present... 

When exiting (from the live session) it did the usual thing and popped open the CD drive door so you can remove the disc.

Am now back in 'normal' ubuntu session and still see the CD drive as unmounted... I just tried a DVD movie - but again nothing...

Any suggestions appreciated!   :confused:

---

### Post by staib on 2007-12-24
> **blueridgedog said:**
> ...I do find it fascinating that at the point in which something breaks, we immediately think "well, it was working before".
You would almost have to think that in order to recognise that it was now **not** working - but I agree - it's stating the obvious!

---

### Post by djrakun on 2007-12-24
I have had similar frustrations with trying to find a dvd-r burner that Ubuntu can recognize immediately.  I had a cyberhome 16x dvd burner that the Gutsy server installation could not recognize ( odd, because the installation disk was IN that optical drive, but halfway through it said "no CD-ROM devices present) I replaced the burner with a generic dvd rom and finished the installation.  I shut down the pc and switched optical drives out.  the eject button works on the cyberhome dvd burner so i put in a disk that I knew worked.  When I tried to mount the drive it says "unable to mount media - there is probably no media in the drive".  I couldn't find any linux drivers for my cyberhome burner so I traded a friend for a (almost) generic NEC burner from probably 5 years ago.  I got the same result - "no media".

Does Ubuntu have bad dvd burner support, or am I just unlucky?

---

### Post by philinux on 2007-12-24
In terminal what does

```
cat /etc/fstab
```

reveal?

---

### Post by staib on 2007-12-24
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=fedce764-010e-4d74-929b-c5985c890006 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=42bed399-8cfe-407e-b928-8d776966e3fc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by philinux on 2007-12-24
> **staib said:**
> 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Well thats exactly the same as mine so no fault there, hmm

---

### Post by tomcheng76 on 2007-12-24
first,open up file broswer, navigate to /dev
is there a file call scd0 ?

second. Go System -> Preference -> Hardware Monitor
Find your DVD drive, mine one is inside 82801DB (ICH4) IDE Controller -> SCSI Host Adaptor -> SCSI DEVICE

Go to details tab , what is the value for the key "block.device" ?

---

### Post by staib on 2007-12-24
**Is there a file call scd0 ?** No

**Go System -> Preference -> Hardware Monitor...** - this launches the Device Manager, but there is nothing here obviously related to a CD/DVD drive...

There is a SATA AHCI Controller which opens into SCSI Host Adapter > SCSI Device > and then 2 entries 'SCSI Generic Interface' and 'ST9xxxxxx' (which is the hard-drive). The next 5 entries seem to be for USB UHCI Controllers plus couple of USB2 controllers (Camera).

I also could not find any Keys that include 'block.device' under the Advanced tab - the first items in the keys column are things like 'info.bus'...

---

### Post by Linuxgenius on 2007-12-24
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=e79db29b-2993-494a-ac7b-1a8e20ce7a19 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=7b203ee8-76ca-4ca0-ad55-638840bd2cd9 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Linuxgenius on 2007-12-24
Go to details tab , what is the value for the key "block.device" ?  mine is /dev/hdc

---

### Post by staib on 2007-12-24
> **Linuxgenius said:**
> Go to details tab , what is the value for the key "block.device" ?  mine is /dev/hdc
Not sure if this helps (but I do appreciate the intent!).
I assume that I am looking for this key within the Device Manager (under the Advanced tab)?

If so there is no reference anywhere under 'Key' to 'block.device' - so I'm unsure what to do next!

---

### Post by tomcheng76 on 2007-12-24
i think you only have one harddrive,right?
if yes, you may try to edit /etc/fstab by issuing the command
> gksudo gedit /etc/fstab
from
> /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
to
> /dev/sdb /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
of coz you can try /dev/hda etc.
if you have 2 harddrives, my first bet would be /dev/sdc

---

### Post by staib on 2007-12-25
Mmmm... thanks Tom.  

You were right - there is one hard-drive (with two two partitions - for Vista and Ubuntu).   

I just tried re-naming that section in fstab as you suggested - but it made no difference. I can see the CD icon under Places > Computer but if I try to mount it the error is "**mount: special device /dev/scd0 does not exist**"  (or sdb when I tried that...)

As I mentioned in an earlier post the weird thing is that **Vista** can no longer see the drive either...  not a big deal as I would be rather using Ubuntu...

I find it hard to believe but I see that others have reported similar experiences - this one goes back to March and was from a Vista/Ubuntu (6.10) user:  " cd/dvd drive was visible when only Vista was installed - it is since Ubuntu was installed as a secondary operating system that it disappeared. ..."   [http://ubuntuforums.org/showthread.php?t=377829]("http://ubuntuforums.org/showthread.php?t=377829")

---

### Post by staib on 2007-12-31
Predictably the only way I can get the vendors to fix Vista for me is to allow them to run the recovery disc which will overwrite the entire hard-drive back to its pre-linux days when Vista was happy seeing the CD/DVD drive.. <sigh>
.
Given the difficulties that I have experienced getting Ubuntu (and other distros) to work out of the box on this particular Lenovo N200 laptop - I'm talking basic things like sound, desktop effects, 'sleeping and waking' - not just nice-to-haves like the fingerprint reader for logging on, and the camera etc. I will be going back to Vista on this laptop. 

A sincere thanks to all who tried to help - you are tribute to this 'other way' - and at least I have Ubuntu on another box to play with :-)
Happy New Year as well.

---

### Post by staib on 2008-03-16
I ran Vista for just under 3 months - it's pretty enough - and the DVD-RW drive was fine - but it was <yawn> oh so slow...   

So back now on 7.10 (on a Lenovo 3000 N200 laptop) :guitar:

But the problem with the CD/DVD persists - and I really need your collective wisdom to get this sorted...

This time I installed 7.10 onto the entire hard-drive...  There is one hard-drive and one built in DVD-RW.  All is good (though I will need help later getting the webcam running) but I really want to crack the error with my unmountable cd/dvd - error "mount: special device /dev/scd0 does not exist"


Any suggestions?

---

### Post by staib on 2008-03-16
Just thought I'd also post the output of fstab

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f735a63a-4a89-4033-b3aa-0fe421c1bf0e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=2d5ea58c-8924-4d36-8e5d-53f1a9d54c02 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by hipotermia on 2008-05-09
since i've upgrade 7.10 to 8.04 by update manager my dvd rom drive doesn't work.

i don't know what to do.

it gives me unable to mount media with any cd/dvd in the drive.

my details are:

> /dev/scd0:

ATAPI CD-ROM, with removable media
	Model Number:       TSSTcorpCD/DVDW TS-H552B                
	Serial Number:      
	Firmware Revision:  TS12    
Standards:
	Likely used CD-ROM ATAPI-1
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
Capabilities:
	LBA, IORDY(cannot be disabled)
	DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=227ns  IORDY flow control=120ns

> 
  *-disk:0                
       description: ATA Disk
       product: Hitachi HDS72161
       vendor: Hitachi
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: P22O
       serial: PV7904ZFSDU25V
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00008d8a
  *-disk:1
       description: ATA Disk
       product: ST3120022A
       vendor: Seagate
       physical id: 0.1.0
       bus info: scsi@2:0.1.0
       logical name: /dev/sdb
       version: 8.01
       serial: 5JT55QP4
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=08eba7ca
  *-cdrom
       description: DVD writer
       product: CD/DVDW TS-H552B
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: TS12
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open



is there anyone who could help?

thanks in advance.

---

