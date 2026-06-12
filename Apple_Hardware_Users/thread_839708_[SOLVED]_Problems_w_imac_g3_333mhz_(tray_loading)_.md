---
title: "[SOLVED] Problems w/ imac g3 333mhz (tray loading) 96mb ram"
date: 2008-06-24
forum: Apple Hardware Users
---

### Post by VitaLiNux on 2008-06-24
I'm having issues with [this imac]("http://www.everymac.com/systems/apple/imac/stats/imac_333.html") that i bought in a flea market, the green one with 333mhz, macOS 8.6 and 96mb of ram . I downloaded a powerpc alternate cd image, md5sum it and it matched with the image @ server I downloaded it from. Good. Then I burned it using Brasero with my ubuntu pc. Problem is I put the cd into the tray, press ¨c¨ button to boot from the disk, but it goes right through Mac OS! (I tried cmd+option+shift+delete with the same result also).

All I need to know is what I am missing/doing wrong! Any ideas?

---

### Post by VitaLiNux on 2008-06-24
> **VitaLiNux said:**
> I'm having issues with [this imac]("http://www.everymac.com/systems/apple/imac/stats/imac_333.html") that i bought in a flea market, the green one with 333mhz, macOS 8.6 and 96mb of ram . I downloaded a powerpc alternate cd image, md5sum it and it matched with the image @ server I downloaded it from. Good. Then I burned it using Brasero with my ubuntu pc. Problem is I put the cd into the tray, press ¨c¨ button to boot from the disk, but it goes right through Mac OS! (I tried cmd+option+shift+delete with the same result also).

All I need to know is what I am missing/doing wrong! Any ideas?

I need to know whether I have an OldWorldMac or a NewWorld one.

---

### Post by VitaLiNux on 2008-06-24
I really need help with it, guys! I want to know the NewWorld/Oldworld thing  to know how to proceed, I have had some experience with Ubuntu and Fedora as well. But any detail you can give me is really appreciated!!

---

### Post by stream303 on 2008-06-24
You've got a "new world" machine, so no problem there.

Make sure that you let brasero burn the image as an iso, and not a general data project.  Also, be sure to use CD-R and not CD-RW media.  And, be sure to burn at very low speeds, something like 2x or 4x.

Sometimes I bypass brasero, and just right-click on the downloaded iso, and use "write to disk" which will automatically take care of the iso image burn - just do it at low speeds onto CD-R.  You may also have to try a different brand of CD-R.

When booting, holding down the "C" key prior to powering up works, and for others, holding down the "C" very quickly *after* powering up, and hold it down long enough to ensure that the cd is actually booting is called for.

With only 96mb of ram, you'll most likely be limited to a very lightweight installation, and may have to resort to using the "server" image, adding a light layer of X on top:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Never mind that the intro is for Intel - it works just as well on PPC.

Also keep in mind that you'll most likely need to edit your /etc/X11/xorg.conf file manually to get X up and running, but we can cross that bridge when you get there.  In addition, if the hard drive isn't oem, but a larger replacement, you may have to do a custom partition to keep root under 8gb, typically 7gb to be safe.

Note that I have no experience dual-booting the older Mac-os with Ubuntu, and generally just let guided partitioning "use the whole disk" - which of course wipes out everything - so if retaining Mac-os is important, you'll need to do a bit more research on that one....

---

### Post by VitaLiNux on 2008-06-24
I have messed 3 cds up! Jeeez! I can't control the burning speed of this thing. It isn't that I don't know how. Problem is I'm just given not good choices. I can say from Brasero that even when selected 1x speed to burn it burned the disc @ 16x(I burned 2 discs bringing me the same result!) and from Nero Linux 3 I got undesirable choices (16x,24x,40x and 46x). I don't know what to do! Heeeeelp!

---

### Post by VitaLiNux on 2008-06-24
> Sometimes I bypass brasero, and just right-click on the downloaded iso, and use "write to disk" which will automatically take care of the iso image burn - just do it at low speeds onto CD-R. You may also have to try a different brand of CD-R.

In fact, I did this and I couldn't even see the control speed there. It burns directly at an automatic speed that way!

---

### Post by stream303 on 2008-06-24
Well, with 96mb of ram, we might as well learn to love the cli. :)

On your Ubuntu-PC, with blank media in the drive, lets try to force it to a very low speed and just do a dummy run so you won't make so many coasters. :)

```
wodim -v -dummy speed=4 ubuntu.iso
```

Where ubuntu.iso is your path to the downloaded iso...  If it chokes on the 4x speed, you can try to force the drive to go as low as it can by changing the speed value to zero:

```
wodim -v -dummy **speed=0** ubuntu.iso
```

If it works on a dry run, just remove the *-dummy* parameter to do a burn.

Somehow you'll need to get your burn speed down to a level that the G3 can handle.

---

### Post by VitaLiNux on 2008-06-25
Maybe you won't believe the following: I was trying everything to make it work, I went after synaptic, found cdrskin, but it didn't work. Tried with the cdrecord command, found @ [http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html) , but it gave me a fast scrolling terminal. Tried again to see the output, and It was what it put:

vitalinux@desktop:~$ cdrecord
wodim: No tracks specified. Need at least one.
Usage: wodim [options] track1...trackn

Use	wodim -help
to get a list of valid options.

Use	wodim blank=help
to get a list of valid blanking options.

Use	wodim dev=b,t,l driveropts=help -checkdrive
to get a list of drive specific options.

Use	wodim dev=help
to get a list of possible SCSI transport specifiers.
station1@yournamehere:~$ wodim -help
Usage: wodim [options] track1...trackn
Options:
	-version	print version information and exit
	dev=target	SCSI target to use as CD/DVD-Recorder
	gracetime=#	set the grace time before starting to write to #.
	timeout=#	set the default SCSI command timeout to #.
	debug=#,-d	Set to # or increment misc debug level
	kdebug=#,kd=#	do Kernel debugging
	-verbose,-v	increment general verbose level by one
	-Verbose,-V	increment SCSI command transport verbose level by one
	-silent,-s	do not print status of failed SCSI commands
	driver=name	user supplied driver name, use with extreme care
	driveropts=opt	a comma separated list of driver specific options
	-setdropts	set driver specific options and exit
	-checkdrive	check if a driver for the drive is present
	-prcap		print drive capabilities for MMC compliant drives
	-inq		do an inquiry for the drive and exit
	-scanbus	scan the SCSI and IDE buses and exit
	-reset		reset the SCSI bus with the cdrecorder (if possible)
	-abort		send an abort sequence to the drive (may help if hung)
	-overburn	allow to write more than the official size of a medium
	-ignsize	ignore the known size of a medium (may cause problems)
	-useinfo	use *.inf files to overwrite audio options.
	speed=#		set speed of drive
	blank=type	blank a CD-RW disc (see blank=help)
	-format		format a CD-RW/DVD-RW/DVD+RW disc
	formattype=#	select the format method for DVD+RW disc
	fs=#		Set fifo size to # (0 to disable, default is 4 MB)
	ts=#		set maximum transfer size for a single SCSI command
	-load		load the disk and exit (works only with tray loader)
	-lock		load and lock the disk and exit (works only with tray loader)
	-eject		eject the disk after doing the work
	-dummy		do everything with laser turned off
	-msinfo		retrieve multi-session info for genisoimage
	-msifile=path	run -msinfo and copy output to file
	-toc		retrieve and print TOC/PMA data
	-atip		retrieve and print ATIP data
	-multi		generate a TOC that allows multi session
			In this case default track type is CD-ROM XA mode 2 form 1 - 2048 bytes
	-fix		fixate a corrupt or unfixated disk (generate a TOC)
	-nofix		do not fixate disk after writing tracks
	-waiti		wait until input is available before opening SCSI
	-immed		Try to use the SCSI IMMED flag with certain long lasting commands
	-force		force to continue on some errors to allow blanking bad disks
	-tao		Write disk in TAO mode.
	-dao		Write disk in SAO mode.
	-sao		Write disk in SAO mode.
	-raw		Write disk in RAW mode.
	-raw96r		Write disk in RAW/RAW96R mode.
	-raw96p		Write disk in RAW/RAW96P mode.
	-raw16		Write disk in RAW/RAW16 mode.
	-clone		Write disk in clone write mode.
	tsize=#		Length of valid data in next track
	padsize=#	Amount of padding for next track
	pregap=#	Amount of pre-gap sectors before next track
	defpregap=#	Amount of pre-gap sectors for all but track #1
	mcn=text	Set the media catalog number for this CD to 'text'
	isrc=text	Set the ISRC number for the next track to 'text'
	index=list	Set the index list for the next track to 'list'
	-text		Write CD-Text from information from *.inf or *.cue files
	textfile=name	Set the file with CD-Text data to 'name'
	cuefile=name	Set the file with CDRWIN CUE data to 'name'
	-audio		Subsequent tracks are CD-DA audio tracks
	-data		Subsequent tracks are CD-ROM data mode 1 - 2048 bytes (default)
	-mode2		Subsequent tracks are CD-ROM data mode 2 - 2336 bytes
	-xa		Subsequent tracks are CD-ROM XA mode 2 form 1 - 2048 bytes
	-xa1		Subsequent tracks are CD-ROM XA mode 2 form 1 - 2056 bytes
	-xa2		Subsequent tracks are CD-ROM XA mode 2 form 2 - 2324 bytes
	-xamix		Subsequent tracks are CD-ROM XA mode 2 form 1/2 - 2332 bytes
	-cdi		Subsequent tracks are CDI tracks
	-isosize	Use iso9660 file system size for next data track
	-preemp		Audio tracks are mastered with 50/15 microseconds preemphasis
	-nopreemp	Audio tracks are mastered with no preemphasis (default)
	-copy		Audio tracks have unlimited copy permission
	-nocopy		Audio tracks may only be copied once for personal use (default)
	-scms		Audio tracks will not have any copy permission at all
	-pad		Pad data tracks with 15 zeroed sectors
			Pad audio tracks to a multiple of 2352 bytes
	-nopad		Do not pad data tracks (default)
	-shorttrack	Subsequent tracks may be non Red Book < 4 seconds if in SAO or RAW mode
	-noshorttrack	Subsequent tracks must be >= 4 seconds
	-swab		Audio data source is byte-swapped (little-endian/Intel)
The type of the first track is used for the toc type.
Currently only form 1 tracks are supported.

---

### Post by VitaLiNux on 2008-06-25
And then I came here to see if somebody posted on this thread. Yeah! I'll tell you, such an odd thing! Well, thanks stream303, I'll try the command above to see what happens, then I'd do it without the 'dummy' thing. BRB!

---

### Post by VitaLiNux on 2008-06-25
The command:
wodim -v -dummy -eject dev=/dev/sr0 speed=4 /media/sdb6/downloadz/ubuntu-6.06-alternate-powerpc.iso 

The output:

wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVD-RAM GSA-H54N'
Revision       : '1.00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0012 (DVD-RAM) 
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
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1114112 = 1088 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Drive DMA Speed: 96286 kB/s 547x CD 69x DVD
FIFO size      : 12582912 = 12288 KB
Track 01: data   691 MB        
Total size:      794 MB (78:43.06) = 354230 sectors
Lout start:      794 MB (78:45/05) = 354230 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 6
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type C, low Beta category (C-) (6)
  ATIP start of lead in:  -11231 (97:32/19)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 27
Manufacturer: Prodisc Technology Inc.
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 5616
Speed set to 2822 KB/s
Starting to write CD/DVD at speed  16.0 in dummy TAO mode for single session.
Last chance to quit, starting dummy write i   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Starting new track at sector: 0
Track 01:  166 of  691 MB written (fifo 100%) [buf  91%]  16.9x.wodim: Caught interrupt.
Writing  time:   93.127s
Min drive buffer fill was 90%
wodim: fifo had 3391 puts and 3200 gets.
wodim: fifo was 0 times empty and 3153 times full, min fill was 95%.
vitalinux@desktop:~$

---

### Post by VitaLiNux on 2008-06-25
Well, I appreciate your help, buddy, but the issue is that I can not burn a cdr @ less than 16x with this dvd burner. Though I have no issues when I try to burn a dvd disk @ 2x or faster. Why is it?

---

### Post by stream303 on 2008-06-26
Man, that's strange.  Did you try "speed=0" to see if it will somehow force it to go lower?

At this point, I dunno' - you might have to burn it on a different box, or maybe a different drive.

Since this is no longer a PPC-specific issue, maybe posting this problem in the Hardware and Laptops forum might get you some wider exposure.  I think I'll head there myself as I'd like to know what is causing this problem too.

Could it just be that your drive on your PC has a minimum-writing speed of 16x no matter what?

---

### Post by Jammy4041 on 2008-06-26
sorry to interrupt, but All PPC iMacs tray loading or whatever **are New World.** That means you have to press C to boot from CD. 

As youare in Mac OS 8, you could try updating your iMac's firmware to the latest version. (2.1, I think). Then burn your Cd the way Stream 303 says on your Ubuntu PC.
 
With 96MB Ram though, I reccommend updating that to 256MB. That's pretty reasonable. 
The RAM you want for is PC100 SDRAM SODIMM

This page may also help [http://www.djonmac.com/ram/upgraderam.html](http://www.djonmac.com/ram/upgraderam.html)

I hope this helps...

---

### Post by VitaLiNux on 2008-06-26
> **stream303 said:**
> Man, that's strange.  Did you try "speed=0" to see if it will somehow force it to go lower?

At this point, I dunno' - you might have to burn it on a different box, or maybe a different drive.

Since this is no longer a PPC-specific issue, maybe posting this problem in the Hardware and Laptops forum might get you some wider exposure.  I think I'll head there myself as I'd like to know what is causing this problem too.

Could it just be that your drive on your PC has a minimum-writing speed of 16x no matter what?

Yes, I did try speed=0 to force it to the lowest speed, but it did not, it changed to 16x. By the way, today I did move the PPC iso to another pc, it has a cdrw that allowed me to burn the disk @ 2x! BUT the imac did not recognize the disk. I've wasted five disks to give a new live to this PowerPC. Geez, I'm almost giving up, because every single, including the last one, after loading MacOS 8.6 it put the following output in a dialog box:

```
this disk is unreadable by this computer. Do you want to initialize the disk?

Name: [untitled]
Format[(a selection box)]  

[Eject]  [Initialize]
```

Nothing to do with it, I suppose.

---

### Post by VitaLiNux on 2008-06-26
Even though I couldn't fix this problem, I really appreciated your help, buddies. Thank you.

---

### Post by stream303 on 2008-06-27
Aha - It doesn't really matter if the old Mac-OS will recognize the disk - all that matters is that you find a way to reboot with the cd in the drive, and hold down the C key on powerup.  If Mac-OS won't let you just "ignore" the cd insertion, or spits it out on reboot, you might just have to see if you can sneak it into the drive during powerup quickly enough for it to get recognized by the system boot process as you hold down the C key before Mac-OS gets a hold of it.  It might require three-hands. :)

I looked at the specs, and they say it is a 24x cdrom, so hopefully it can boot with a cd burned at 16x.  Worth a shot anyway.  I know you've tried it before, but I wonder if the Mac-OS was getting in your way, or somehow trying to preserve itself with some possibly misleading info. :)

I'm sure you've burned it as an iso right - where after the burn if you look at it with your Ubuntu-PC, it shows up as a whole filesystem full of files and directories, rather than just one single iso file?

Crossing fingers...

---

### Post by abtabt on 2008-06-27
hello 
can you get the cd on the desktop and see whats in it if you boot in MAC OS ????

---

### Post by VitaLiNux on 2008-06-30
Guys, I gave up with it. I got a Mac OS 9.1 disk from someone, upgraded it and let it that way. IT DID BOOTED THE MACOS9.1 DISK FROM THE VERY BEGINNING. Dunno what could be the issue. Well, next time will try something less old. :confused::)

---

