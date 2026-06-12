---
title: "Burner not working on 7.04"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by bodam on 2007-05-05
So I'm new to Linux so I'm not sure how to troubleshoot this but I can't burn CDs or DVDs.   The drive works fine as a CD and DVD drive, but I can't burn even though it is recognized as a burner drive.   If I use burn tools, it correctly identifies the media types the drive supports.

It's fustrating because it's the only hardware that I have not been able to get working.  Any suggestions would be appreciated.

Dave

---

### Post by nalmeth on 2007-05-06
What kind of errors do you get when trying to burn?

---

### Post by bodam on 2007-05-06
It keeps asking me to insert writable media.  I never had an issue with this drive with Windows.....

---

### Post by oilchangeguy on 2007-05-06
are you using cd/r, or cd/rw disc's?

---

### Post by bodam on 2007-05-06
Iv'e tried CD-R CD-RW, DVD-R and DVD-RW.  None work.

---

### Post by nalmeth on 2007-05-07
Hey, I don't know much about how to solve your problem, because I've never had anything like this happen (across multiple PC's and burners).

Anyway, try this command in the terminal (Applications -> Accessories -> Terminal)
```
sudo hdparm /dev/hdc
```It will tell you if Direct Media Access is enabled for the drive. I don't think that alone is the problem, but then again, it may be afterall.
Post the output of the command here.

Just so you know I'm not tricking you into something, here is the page on DMA
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

I add this only because I worry sometimes about how people are given command-line instructions, without much explanation of what they're doing.

---

### Post by bodam on 2007-05-07
Here's what I get from running the command:

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

Any suggestions??

Dave

---

### Post by rem on 2007-05-08
> **bodam said:**
> Here's what I get from running the command:

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

Any suggestions??

Dave

Exactly the same issue and error here Dave!
I recently upgraded to Feisty and cannot burn anything anymore ... while I was under Dapper the DVD-RW worked flawlessly.  I will watch this post and really hope somebody here will be able to help ...

Thanks,

Rem.

---

### Post by Darko-TheRaven on 2007-05-08
i was just about to post about the same problem. I am however dual booting feisty with dapper as a solution for now.

---

### Post by bodam on 2007-05-09
Sorry that you're both having the same problem, but at the same time, I'm glad that I'm not the only one.  I hope someone has a fix.  Everything else works flawlessly.  

Dave

---

### Post by whitefort on 2007-05-09
No solution here, sorry - this is just a 'me too' post to let you guys know you're not alone.

I'd actually not tried to burn any CDs until I saw this post - but now I find I have the exact same error.

Fingers crossed that someone can find a fix soon.  If I come up with anything, I'll report back.

---

### Post by rem on 2007-05-09
> Everything else works flawlessly.

Not quite here. Had some [nVidia issues]("http://ubuntuforums.org/showthread.php?t=434746") in Feisty as well.. Dapper seemed way more stable.
Of course is a step forward, much more faster and hopefully with some patches and fixes more reliable in the future.

---

### Post by rem on 2007-05-09
> **whitefort said:**
> No solution here, sorry - this is just a 'me too' post to let you guys know you're not alone.

I'd actually not tried to burn any CDs until I saw this post - but now I find I have the exact same error.

Fingers crossed that someone can find a fix soon.  If I come up with anything, I'll report back.

Until then, we should find someone to burn our CD/DVDs :D

---

### Post by trotur on 2007-05-09
Here might be solution (at least for nautilus-cd-burner).

See [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/66254](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/66254)
To confirm that you are affected by that bug, put some cd in your drive and run in terminal /usr/lib/nautilus-cd-burner/list_cddrives . If you get "-- WARNING **: No property volume.disc.capacity on device --", this should help.

Do as follows (little edited from [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/66254/comments/33](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/66254/comments/33))

1. Make two new files:
First file (for CD-Rs):
```
sudo gedit /etc/hal/fdi/information/cd-r.fdi
```
Put following in the file and save.
```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
	<device>
		<match key="@info.parent:storage.cdrom.cdr" bool="true">
			<match key="block.is_volume" bool="true">
				<match key="volume.disc.type" string="unknown">
					<match key="volume.disc.is_rewritable" bool="false">
						<match key="volume.disc.is_blank" bool="true">
							<merge key="volume.disc.type" type="string">cd_r</merge>
							<merge key="volume.disc.capacity" type="uint64">736970752</merge>
						</match>
					</match>
				</match>
			</match>
		</match>
	</device>
</deviceinfo>
```
Second file (for CD-RWs):
```
sudo gedit /etc/hal/fdi/information/cd-rw.fdi
```
Put following in the file and save.
```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
        <device>
                <match key="@info.parent:storage.cdrom.cdrw" bool="true">
               		<match key="block.is_volume" bool="true">
                	        <match key="volume.disc.type" string="unknown">
                	                <match key="volume.disc.is_rewritable" bool="true">
                	                        <merge key="volume.disc.type" type="string">cd_rw</merge>
                	                        <merge key="volume.disc.capacity" type="uint64">736970752</merge>
                	                </match>
                	        </match>
               		</match>
                </match>
        </device>
</deviceinfo>
```

2. Put some cd-r or cd-rw to your drive and see if you can burn/blank disk.

Hope this helps.

PS. This isn't final solution. For example, I don't know what burner will like about 650mb cd (note that capacity is set to 700mb in above files).

---

### Post by rem on 2007-05-09
Not the case here... must be something else because when I run

> /usr/lib/nautilus-cd-burner/list_cddrives

I get a list of parameters which seem to be accurate but this one must be blocking me from burning media:

> is mounted:           FALSE

How can it be not mounted since the volume icon is on the desktop???

---

### Post by rem on 2007-05-09
> **rem said:**
> Not the case here... must be something else because when I run
I get a list of parameters which seem to be accurate but this one must be blocking me from burning media:
How can it be not mounted since the volume icon is on the desktop???

I just tried to mount it and it doesn't seem to be working. The terminal output is


> mount: wrong fs type, bad option, bad superblock on /dev/hdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

and dmesg | tail shows: 

> 
[42347.752903] hdb: rw=0, want=68, limit=4
[42347.760104] attempt to access beyond end of device
[42347.760114] hdb: rw=0, want=1252, limit=4
[42347.760295] attempt to access beyond end of device
[42347.760298] hdb: rw=0, want=1028, limit=4
[42347.760454] UDF-fs: No partition found (1)
[42347.866992] attempt to access beyond end of device
[42347.867002] hdb: rw=0, want=68, limit=4
[42347.867180] isofs_fill_super: bread failed, dev=hdb, iso_blknum=16, block=16
[42349.038040] Inbound IN=eth1 OUT= MAC=00:50:fc:6a:3e:3a:00:19:2f:e5:f2:05:08:00 SRC=89.137.171.203 DST=89.137.3.223 LEN=64 TOS=0x00 PREC=0x00 TTL=45 ID=8154 DF PROTO=TCP SPT=2911 DPT=139 
WINDOW=53760 RES=0x00 SYN URGP=0

Can anybody please help?

Thanks.

---

### Post by trotur on 2007-05-09
> **rem said:**
> > is mounted: FALSEHow can it be not mounted since the volume icon is on the desktop???

Running */usr/lib/nautilus-cd-burner/list_cddrives* unmounts cd-drive and thus removes the icon from desktop and gives "is mounted: FALSE" (at least for me it does).

Can you burn/blank discs with cdrecord?

---

### Post by bodam on 2007-05-09
I ran the command suggested and I have posted the results below.  Being new to Linux I'm out of my depth.  The settings look mostly OK.   BTW:  Yes I do have two drives.


bodam@bodam-desktop:~$ /usr/lib/nautilus-cd-burner/list_cddrives
Drive:
  name:                 IDE-DVD DROM6216
  device:               /dev/hdd
  door:                 closed
  type:                 CD, DVD
  is mounted:           FALSE
  max read speed:       7040 KiB/s (CD 46.9x, DVD 5.2x)
  max write speed:      0 KiB/s (CD 0.0x, DVD 0.0x)
  write speeds:
Media:
  label:                ''
  type:                 Couldn't open media
  is writable:          FALSE
  is appendable:        FALSE
  capacity:             Could not be determined
  size:                 Could not be determined
---
Drive:
  name:                 HP DVD Writer 840b
  device:               /dev/hdc
  door:                 closed
  type:                 CD-R, CD-RW, DVD-RAM, DVD-R, DVD-RW, DVD+R, DVD+R DL, DVD+RW, CD, DVD
  is mounted:           FALSE
  max read speed:       7056 KiB/s (CD 47.0x, DVD 5.2x)
  max write speed:      7056 KiB/s (CD 47.0x, DVD 5.2x)
  write speeds:         7050 KiB/s (CD 47.0x, DVD 5.2x)
                        6900 KiB/s (CD 46.0x, DVD 5.1x)
                        6750 KiB/s (CD 45.0x, DVD 4.9x)
                        6600 KiB/s (CD 44.0x, DVD 4.8x)
                        6450 KiB/s (CD 43.0x, DVD 4.7x)
                        6300 KiB/s (CD 42.0x, DVD 4.6x)
                        6150 KiB/s (CD 41.0x, DVD 4.5x)
                        6000 KiB/s (CD 40.0x, DVD 4.4x)
                        5850 KiB/s (CD 39.0x, DVD 4.3x)
                        5700 KiB/s (CD 38.0x, DVD 4.2x)
                        5550 KiB/s (CD 37.0x, DVD 4.1x)
                        5400 KiB/s (CD 36.0x, DVD 3.9x)
                        5250 KiB/s (CD 35.0x, DVD 3.8x)
                        5100 KiB/s (CD 34.0x, DVD 3.7x)
                        4950 KiB/s (CD 33.0x, DVD 3.6x)
                        4800 KiB/s (CD 32.0x, DVD 3.5x)
                        4650 KiB/s (CD 31.0x, DVD 3.4x)
                        4500 KiB/s (CD 30.0x, DVD 3.3x)
                        4350 KiB/s (CD 29.0x, DVD 3.2x)
                        4200 KiB/s (CD 28.0x, DVD 3.1x)
                        4050 KiB/s (CD 27.0x, DVD 2.9x)
                        3900 KiB/s (CD 26.0x, DVD 2.8x)
                        3750 KiB/s (CD 25.0x, DVD 2.7x)
                        3600 KiB/s (CD 24.0x, DVD 2.6x)
                        3450 KiB/s (CD 23.0x, DVD 2.5x)
                        3300 KiB/s (CD 22.0x, DVD 2.4x)
                        3150 KiB/s (CD 21.0x, DVD 2.3x)
                        3000 KiB/s (CD 20.0x, DVD 2.2x)
                        2850 KiB/s (CD 19.0x, DVD 2.1x)
                        2700 KiB/s (CD 18.0x, DVD 1.9x)
                        2550 KiB/s (CD 17.0x, DVD 1.8x)
                        2400 KiB/s (CD 16.0x, DVD 1.7x)
                        2250 KiB/s (CD 15.0x, DVD 1.6x)
                        2100 KiB/s (CD 14.0x, DVD 1.5x)
                        1950 KiB/s (CD 13.0x, DVD 1.4x)
                        1800 KiB/s (CD 12.0x, DVD 1.3x)
                        1650 KiB/s (CD 11.0x, DVD 1.2x)
                        1500 KiB/s (CD 10.0x, DVD 1.1x)
                        1350 KiB/s (CD 9.0x, DVD 0.9x)
                        1200 KiB/s (CD 8.0x, DVD 0.8x)
                        1050 KiB/s (CD 7.0x, DVD 0.7x)
                        900 KiB/s (CD 6.0x, DVD 0.6x)
                        750 KiB/s (CD 5.0x, DVD 0.5x)
                        600 KiB/s (CD 4.0x, DVD 0.4x)
                        450 KiB/s (CD 3.0x, DVD 0.3x)
                        300 KiB/s (CD 2.0x, DVD 0.2x)
                        150 KiB/s (CD 1.0x, DVD 0.1x)

Media:
  label:                ''
  type:                 Couldn't open media
  is writable:          FALSE
  is appendable:        FALSE
  capacity:             Could not be determined
  size:                 Could not be determined
---
bodam@bodam-desktop:~$

---

### Post by trotur on 2007-05-09
Please put some cd into your burn-capable drive (HP DVD Writer 840b), wait till it is mounted (cd-icon appears to your desktop) and then run again /usr/lib/nautilus-cd-burner/list_cddrives and post the output here.

---

### Post by rem on 2007-05-09
> **trotur said:**
> Running */usr/lib/nautilus-cd-burner/list_cddrives* unmounts cd-drive and thus removes the icon from desktop and gives "is mounted: FALSE" (at least for me it does).
Can you burn/blank discs with cdrecord?

I see now... sorry for my ignorance.
I can't burn anything. I tried to blank a CD-RW  to format DVD-RWs... to burn regular CDs and DVDs but none of this is working :(
I tried to burn some data with the nautilus burner and with Gnome Baker as well and nothing. Both of them used to work properly under Dapper!

Thanks.

---

### Post by bodam on 2007-05-09
The 1st run was with a blank burnable CD.  This time there is a music CD in the drive....


bodam@bodam-desktop:~$ /usr/lib/nautilus-cd-burner/list_cddrives
Drive:
  name:                 IDE-DVD DROM6216
  device:               /dev/hdd
  door:                 closed
  type:                 CD, DVD
  is mounted:           FALSE
  max read speed:       7040 KiB/s (CD 46.9x, DVD 5.2x)
  max write speed:      0 KiB/s (CD 0.0x, DVD 0.0x)
  write speeds:
Media:
  label:                ''
  type:                 Couldn't open media
  is writable:          FALSE
  is appendable:        FALSE
  capacity:             Could not be determined
  size:                 Could not be determined
---
Drive:
  name:                 HP DVD Writer 840b
  device:               /dev/hdc
  door:                 closed
  type:                 CD-R, CD-RW, DVD-RAM, DVD-R, DVD-RW, DVD+R, DVD+R DL, DVD+RW, CD, DVD
  is mounted:           FALSE
  max read speed:       7056 KiB/s (CD 47.0x, DVD 5.2x)
  max write speed:      7056 KiB/s (CD 47.0x, DVD 5.2x)
  write speeds:         7050 KiB/s (CD 47.0x, DVD 5.2x)
                        6900 KiB/s (CD 46.0x, DVD 5.1x)
                        6750 KiB/s (CD 45.0x, DVD 4.9x)
                        6600 KiB/s (CD 44.0x, DVD 4.8x)
                        6450 KiB/s (CD 43.0x, DVD 4.7x)
                        6300 KiB/s (CD 42.0x, DVD 4.6x)
                        6150 KiB/s (CD 41.0x, DVD 4.5x)
                        6000 KiB/s (CD 40.0x, DVD 4.4x)
                        5850 KiB/s (CD 39.0x, DVD 4.3x)
                        5700 KiB/s (CD 38.0x, DVD 4.2x)
                        5550 KiB/s (CD 37.0x, DVD 4.1x)
                        5400 KiB/s (CD 36.0x, DVD 3.9x)
                        5250 KiB/s (CD 35.0x, DVD 3.8x)
                        5100 KiB/s (CD 34.0x, DVD 3.7x)
                        4950 KiB/s (CD 33.0x, DVD 3.6x)
                        4800 KiB/s (CD 32.0x, DVD 3.5x)
                        4650 KiB/s (CD 31.0x, DVD 3.4x)
                        4500 KiB/s (CD 30.0x, DVD 3.3x)
                        4350 KiB/s (CD 29.0x, DVD 3.2x)
                        4200 KiB/s (CD 28.0x, DVD 3.1x)
                        4050 KiB/s (CD 27.0x, DVD 2.9x)
                        3900 KiB/s (CD 26.0x, DVD 2.8x)
                        3750 KiB/s (CD 25.0x, DVD 2.7x)
                        3600 KiB/s (CD 24.0x, DVD 2.6x)
                        3450 KiB/s (CD 23.0x, DVD 2.5x)
                        3300 KiB/s (CD 22.0x, DVD 2.4x)
                        3150 KiB/s (CD 21.0x, DVD 2.3x)
                        3000 KiB/s (CD 20.0x, DVD 2.2x)
                        2850 KiB/s (CD 19.0x, DVD 2.1x)
                        2700 KiB/s (CD 18.0x, DVD 1.9x)
                        2550 KiB/s (CD 17.0x, DVD 1.8x)
                        2400 KiB/s (CD 16.0x, DVD 1.7x)
                        2250 KiB/s (CD 15.0x, DVD 1.6x)
                        2100 KiB/s (CD 14.0x, DVD 1.5x)
                        1950 KiB/s (CD 13.0x, DVD 1.4x)
                        1800 KiB/s (CD 12.0x, DVD 1.3x)
                        1650 KiB/s (CD 11.0x, DVD 1.2x)
                        1500 KiB/s (CD 10.0x, DVD 1.1x)
                        1350 KiB/s (CD 9.0x, DVD 0.9x)
                        1200 KiB/s (CD 8.0x, DVD 0.8x)
                        1050 KiB/s (CD 7.0x, DVD 0.7x)
                        900 KiB/s (CD 6.0x, DVD 0.6x)
                        750 KiB/s (CD 5.0x, DVD 0.5x)
                        600 KiB/s (CD 4.0x, DVD 0.4x)
                        450 KiB/s (CD 3.0x, DVD 0.3x)
                        300 KiB/s (CD 2.0x, DVD 0.2x)
                        150 KiB/s (CD 1.0x, DVD 0.1x)

Media:
  label:                ''
  type:                 Commercial CD or Audio CD (has-audio)
  is writable:          FALSE
  is appendable:        FALSE
  capacity:             441.60 MiB approx. or 50 mins 17 secs
  size:                 441.60 MiB approx. or 50 mins 17 secs
---

---

### Post by trotur on 2007-05-09
I think you both, rem and bodam, might be having some other burning problem than I had.

Before any fix my outputs' Media-section were for empty cd-rw:
Media:
  label:                ''
  type:                 [COLOR="Red"]Unknown Media[/COLOR] (rewritable) (blank)
  is writable:          [COLOR="Red"]FALSE[/COLOR]
  is appendable:        FALSE
  capacity:             [COLOR="Red"]Could not be determined[/COLOR]
  size:                 0.00 MiB

My problems' sources are on red above.

After [fix]("http://ubuntuforums.org/showthread.php?p=2622510") I got:
Media:
  label:                ''
  type:                 CD-RW (rewritable) (blank)
  is writable:          TRUE
  is appendable:        FALSE
  capacity:             702.83 MiB approx. or 80 mins 6 secs
  size:                 0.00 MiB approx. or 0 mins 0 secs

You may want to try blank some of your cd-rws (or burn something) in terminal running "cdrecord blank=fast dev=/dev/hdX", where hdX is your drive. It'll generate some useful debugging info.

---

### Post by rem on 2007-05-09
> cdrecord blank=fast dev=/dev/hdX

It worked ... also, I was able to erase and write data on a CD-RW with Gnome Baker, but tried a DVD-RW and failed again ... I have a few DVD-RWs and I'm thinking that they might be messed up because of all the writing / formating testing I did today... But since I tried some new DVD-Rs and didn't worked, still I think something might be wrong though ... :(

---

### Post by steve.horsley on 2007-05-09
I remember a while ago (maybe 6 months) there was a problem where DVD-Rs could not be written but DVD+Rs could. I never read anythong about a resolution on this, so maybe the problem persists? Since our DVD decorder (on the telly) only burns +Rs anyway, I don't have any -Rs in the house to check.

---

### Post by bodam on 2007-05-10
Here are my results.  Any suggestions?

bodam@bodam-desktop:~$ cdrecord blank=fast dev=/dev/hdc
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'HP      '
Identification : 'DVD Writer 840b '
Revision       : 'HI86'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Errno: 0 (Success), test unit ready scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0E 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 40s
wodim: No disk / Wrong disk!
bodam@bodam-desktop:~$

---

### Post by kabads on 2007-05-10
Same error here.

---

### Post by bodam on 2007-05-11
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/6415](https://answers.launchpad.net/ubuntu/+question/6415) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Just to let everyone know, I've posted this problem over at Launchpad].  I will let you know if I hear anything....

---

### Post by bodam on 2007-05-11
I went ahead and opened up a bug report for this on Launchpad( #114122..

---

### Post by rem on 2007-05-11
Great!
Hopefully it's going to be fixed. I had the same thing in mind to do today ...

---

### Post by moopere on 2007-05-20
> **trotur said:**
> You may want to try blank some of your cd-rws (or burn something) in terminal running "cdrecord blank=fast dev=/dev/hdX", where hdX is your drive. It'll generate some useful debugging info.

Great advice, thanks a lot.

Somehow Feisty has been blanking discs and making them unreadable, even under windows/nero!  Ahhhh.

Your advice above seems to have restored my CDRW and DVDRW to a useable condition again.

Cheers,
Craig

---

### Post by RobsterUK on 2007-05-22
I'm also having problems burning CDs with GnomeBaker and Nautilus

> /usr/lib/nautilus-cd-burner/list_cddrives
Drive:
  name:                 DVD-ROM SD-R1002
  device:               /dev/scd0
  door:                 closed
  type:                 CD-R, CD-RW, CD, DVD
  is mounted:           FALSE
  max read speed:       4233 KiB/s (CD 28.2x, DVD 3.1x)
  max write speed:      706 KiB/s (CD 4.7x, DVD 0.5x)
  write speeds:         600 KiB/s (CD 4.0x, DVD 0.4x)
                        450 KiB/s (CD 3.0x, DVD 0.3x)
                        300 KiB/s (CD 2.0x, DVD 0.2x)
                        150 KiB/s (CD 1.0x, DVD 0.1x)

Media:
  label:                ''
  type:                 CD-R (blank)
  is writable:          TRUE
  is appendable:        FALSE
  capacity:             701.00 MiB approx. or 80 mins 0 secs
  size:                 0.00 MiB approx. or 0 mins 0 secs


Gnomebaker
> Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 14 00 00 00 00 0E 09 0C 00 50 00 03 00 00
Sense Key: 0x4 Hardware Error, Segment 11
Sense Code: 0x00 Qual 0x03 (setmark detected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.489s timeout 60s
wodim: OPC failed.
Writing  time:    5.052s

Is there a fix for this?

---

### Post by bierholen on 2007-05-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/114122](https://bugs.launchpad.net/ubuntu/+bug/114122) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I also experience serious burn issues under Feisty. I can't burn anything. I think my problems goes back to Feisty handling my burner as SCSI device: 

QSI DVD+-RW SDW-082 LX51 (/dev/scd0, )

It works fine under openSUSE 10.2 where it is mounted as IDE drive (/dev/hdc). Also related to this, there are no burning problems with Feisty on a 5 year old laptop where the burner  is handled as IDE device (/dev/hdc). I appended my error messages (see below) to Bug #114122. I'm not sure, though, if it's really the same bug.

Error message: ( K3b, GnomeBaker, Brasero, Nero, xcdroast):

```



K3b 1.0: CD-R

System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-15-generic
Devices
-----------------------
QSI DVD+-RW SDW-082 LX51 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R16, RAW/R96R, Restricted Overwrite]

K3bIsoImager
-----------------------
mkisofs print size result: 357483 (732125184 bytes)
Pipe throughput: 276400896 bytes read, 276396544 bytes written.

Used versions
-----------------------
mkisofs: 1.1.2
cdrecord: 1.1.2

cdrecord
-----------------------
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'QSI     '
Identification : 'DVD+-RW SDW-082 '
Revision       : 'LX51'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0000 (Reserved/Unknown) 
Profile: 0x0000 (Reserved/Unknown) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
Drive buf size : 1073152 = 1048 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 2822 KB/s
Track 01: data   698 MB        
Total size:      801 MB (79:26.44) = 357483 sectors
Lout start:      802 MB (79:28/33) = 357483 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 2363
Starting to write CD/DVD at speed  16.0 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Errno: 5 (Input/output error), read track info scsi sendcmd: no error
CDB:  52 01 00 00 00 FF 00 00 1C 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 28
cmd finished after 0.002s timeout 240s
/usr/bin/wodim: Cannot get next writable address for 'invisible' track.
/usr/bin/wodim: This means that we are checking recorded media.
/usr/bin/wodim: This media cannot be written in streaming mode anymore.
/usr/bin/wodim: If you like to write to 'preformatted' RW media, try to blank the media first.
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  698 MB written.
Track 01:    1 of  698 MB written (fifo 100%) [buf  87%]   3.7x.

[...]

Track 01:  251 of  698 MB written (fifo  99%) [buf  84%]  11.3x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 01 F7 DF 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 37.540s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 264173568 bytes
Writing  time:  215.654s
Average write speed  22.1x.
Min drive buffer fill was 63%
Fixating...
Fixating time:    0.007s


GnomeBaker 0.6: CD-R

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
TOC Type: 3 = CD-ROM XA mode 2
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'QSI     '
Identification : 'DVD+-RW SDW-082 '
Revision       : 'LX51'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
Drive buf size : 1073152 = 1048 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 2822 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 01 77 83 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 47 00 00 00 00 0E 09 0C 00 00 00 01 00 00
Sense Key: 0x7 Data Protect, Segment 11
Sense Code: 0x00 Qual 0x01 (filemark detected) Fru 0x0
Sense flags: Blk 0 (not valid) end of medium 
resid: 63488
cmd finished after 0.639s timeout 40s
wodim: A write error occured.
wodim: Please properly read the error message above.

write track data: error after 196876288 bytes
Writing  time:  149.320s
Average write speed  31.9x.
Min drive buffer fill was 87%
Fixating...
Fixating time:   37.929s


Brassero Brasero 0.5.2: DVD-R

imager (BraseroLocalImage) set_output
job (BraseroLocalImage) set_task
imager (BraseroLocalImage) get_track
job (BraseroLocalImage) set_task
Session starting:
	flags			= 16727 
	media type	= 0
	speed		= 3
	track type		= 8
	track format	= 2
	output		= none
job (BraseroGrowisofs) set_rate
recorder (BraseroGrowisofs) set_drive
recorder (BraseroGrowisofs) set_flags
job (BraseroGrowisofs) set_source
job (BraseroGrowisofs) set_task
recorder (BraseroGrowisofs) record
process (BraseroGrowisofs) getting varg
growisofs (BraseroGrowisofs) set_action
process (BraseroGrowisofs) got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-speed=3
	-dvd-compat
	-use-the-force-luke=tty
	-Z
	/dev/scd0=/*/*.iso
process (BraseroGrowisofs) launching command
process (BraseroGrowisofs) stdout: Executing 'builtin_dd if=/*/*.iso of=/dev/scd0 obs=32k seek=0'
process (BraseroGrowisofs) stderr: /dev/scd0: engaging DVD-R DAO upon user request...
process (BraseroGrowisofs) stderr: /dev/scd0: reserving 1135069 blocks
process (BraseroGrowisofs) stderr: /dev/scd0: "Current Write Speed" is 4.1x1352KBps.
process (BraseroGrowisofs) stdout:           0/2324621312 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
process (BraseroGrowisofs) stdout:           0/2324621312 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
process (BraseroGrowisofs) stdout:           0/2324621312 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
process (BraseroGrowisofs) stdout:           0/2324621312 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
process (BraseroGrowisofs) stdout:           0/2324621312 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
process (BraseroGrowisofs) stdout:           0/2324621312 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
process (BraseroGrowisofs) stdout:           0/2324621312 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
process (BraseroGrowisofs) stdout:           0/2324621312 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
process (BraseroGrowisofs) stdout:      655360/2324621312 ( 0.0%) @0.1x, remaining 1950:20 RBU 100.0% UBU   4.8%
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_rate
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stdout:      655360/2324621312 ( 0.0%) @0.0x, remaining 2127:39 RBU 100.0% UBU 100.0%
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_rate
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress

[...]

process (BraseroGrowisofs) stdout:   638844928/2324621312 (27.5%) @0.0x, remaining 12:03 RBU 100.0% UBU 100.0%
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_rate
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr: :-[ WRITE@LBA=4cca0h failed with SK=7h/ASC=00h/ACQ=01h]: Input/output error
process (BraseroGrowisofs) stderr: :-( write failed: Input/output error
job (BraseroGrowisofs) asked to stop
	status	= 1
	error		= 1
	message	= "Unhandled error, aborting"
iter (BraseroGrowisofs) stopping
process (BraseroGrowisofs) got killed
iter (BraseroGrowisofs) stopped
job (BraseroGrowisofs) got out of loop
job (BraseroGrowisofs) set_task
Session error : Unhandled error, aborting

[...]

Nero 3.0.0.0 beta: DVD-R

Linux 2.6.20-15-generic
Nero API version: 7.5.14.2
Using interface version: 7.5.0.2
Installed in: /usr/lib/nero/
Application: Nero AG\Nero Linux
Internal Version: 7, 5, 14, 2

Recorder:             <QSI DVD+-RW SDW-082>     Version: LX51 - HA 1 TA 0 - 0.0.0.0
 Adapter driver:      <ata_piix>                HA 1
 Drive buffer  :      2048kB
 Bus Type      :      default (0) -> SCSI, detected: ?
Excluded drive IDs: 
WriteBufferSize: 83886080 (0) Byte
BUFE           : 0
Physical memory     : 1248MB (1278524kB)
Free physical memory: 104MB (107404kB)
Memory in use       : 91 %
Uncached PFiles: 0x0
Use Inquiry    : 1
Global Bus Type: default (0)
Check supported media : Disabled (0) 

22.5.2007
NeroAPI
08:23:51 PM	#1 Text 0 File Burncd.cpp, Line 3490
	Turn on Disc-At-Once, using DVD media
	
08:23:52 PM	#2 Text 0 File DlgWaitCD.cpp, Line 307
	Last possible write address on media:  2298495 (510:46.45, 4489MB)
	Last address to be written:            1135068 (252:14.18, 2216MB)
	
08:23:52 PM	#3 Text 0 File DlgWaitCD.cpp, Line 319
	Write in overburning mode: NO
	
08:23:52 PM	#4 Text 0 File DlgWaitCD.cpp, Line 2951
	Recorder: QSI DVD+-RW SDW-082, Media type: DVD-R
	 Disc Manufacturer: RITEKF - 1
	 Disc Application Code: 64, Disc Physical Code: 193
	
08:23:52 PM	#5 Text 0 File DlgWaitCD.cpp, Line 493
	>>> Protocol of DlgWaitCD activities: <<<
	=========================================
	
08:23:52 PM	#6 Text 0 File ThreadedTransferInterface.cpp, Line 792
	Setup items (after recorder preparation)
	 0: TRM_DATA_MODE1 (2 - CD-ROM Mode 1, ISO 9660)
	    2 indices, index0 (150) not provided
	    original disc pos #0 + 1135069 (1135069) = #1135069/252:14.19
	    not relocatable, disc pos for caching/writing not required/not required
	    -> TRM_DATA_MODE1, 2048, config 0, wanted index0 0 blocks, length 1135069 blocks [QSI DVD+-RW SDW-082 (H:1 T:0)]
	--------------------------------------------------------------
	
08:23:52 PM	#7 Text 0 File ThreadedTransferInterface.cpp, Line 995
	Prepare [QSI DVD+-RW SDW-082 (H:1 T:0)] for write in CUE-sheet-DAO
	DAO infos:
	==========
	 MCN: ""
	 TOCType: 0x00; Session Closed, disc fixated
	 Tracks 1 to 1:                                  Idx 0         Idx 1      Next Trk
	   1: TRM_DATA_MODE1, 2048/0x00, FilePos             0             0    2324621312, ISRC ""
	DAO layout:
	===========
	 ___Start_|____Track_|_Idx_|_CtrlAdr_|_____Size_|______NWA_|_RecDep__________
	        0 |  lead-in |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   1 |    0x41 |  1135069 |  1135069 | 0x00
	  1135069 | lead-out |   1 |    0x41 |        0 |        0 | 0x00
	
08:23:52 PM	#8 Text 0 File Burncd.cpp, Line 4263
	Caching options: cache CDRom or Network-No, small files-Yes (<32KB)
	
08:23:52 PM	#9 Phase 24 File ExtendedProgress.cpp, Line 537
	Caching of files started
	
08:23:52 PM	#10 Text 0 File Burncd.cpp, Line 4382
	Cache writing successful.
	
08:23:52 PM	#11 Phase 25 File ExtendedProgress.cpp, Line 537
	Caching of files completed
	
08:23:52 PM	#12 Phase 36 File ExtendedProgress.cpp, Line 537
	Burn process started at 4x (5540 KB/s)
	
08:23:52 PM	#13 Text 0 File ThreadedTransferInterface.cpp, Line 2712
	Verifying disc position of item 0 (not relocatable, no disc pos, no patch infos, orig at #0): write at #0
	
08:23:52 PM	#14 Text 0 File DVDR.cpp, Line 3151
	Recording mode: Sequential Recording Mode
	
08:23:52 PM	#15 Text 0 File DVDR.cpp, Line 3307
	Start write address at LBA 0
	DVD high compatibility mode: Yes
	
08:23:52 PM	#16 Text 0 File Cdrdrv.cpp, Line 9885
	---- Disc Structure: Physical Format Information (00h) ----
	Media Type: 0, Layer: 0, Address: 0 (0 h), AGID: 0; Length: 2050
	 Book Type: DVD-R (2), Part Version: 2.0x (5), Extended Part Version: 2.1 (33)
	 Disc Size: 120 mm,      Maximum Rate: <not specified> (F h)
	 Number of Layers: 1,    Track Path: Parallel Track Path (PTP),  Layer Type: recordable
	 Linear Density:         0,267 um/bit,  Track Density:  0,74 um/track
	 Starting Physical Sector Number of Data Area: 30000 h (DVD-ROM, DVD-R/-RW, DVD+R/+RW)
	 End Sector Number in Layer 0:                 0 h (LBN: FFFD0000 h, 4193920 MB)
	 Data in Burst Cutting Area (BCA) does not exist
	  Revision number of maximum recording speed: 6.0
	  Revision number of minimum recording speed: -
	  Revision number table of recording speed: 1.0 2.0 3.0 4.0 5.0 - - 
	  Class: 0
	  Start sector number of the current Border-Out: 2FE10 h
	  Start sector number of the next Border-In:     2FFA0 h
	 Media Specific [16..63]:
	    00 60 00 10 20 30 40 50 - 00 00 00 21 00 00 00 00    .`...0@P...!....
	    00 02 FE 10 00 02 FF A0 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	
08:23:52 PM	#17 Text 0 File ThreadedTransfer.cpp, Line 269
	Pipe memory size 83836800
	
08:23:53 PM	#18 Text 0 File Cdrdrv.cpp, Line 1347
	20:23:53 - QSI DVD+-RW SDW-082 (H:1 T:0) : Queue again later
	
08:32:13 PM	#19 SCSI -400 File SCSIInterface.cpp, Line 622
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xaee0bc40
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x02 (0x01, SCSI_TASTATUS_CHKCOND)
	Sense Key:  0x07 (Unknown)
	Sense Code: 0x00
	Sense Qual: 0x01
	CDB Data:   0x2A 0x00 0x00 0x0E 0xC8 0x40 0x00 0x00 0x20 0x00 
	Sense Data: 0x72 0x0B 0x47 0x00 0x00 0x00 0x00 0x0E 
	            0x09 0x0C 0x00 0x00 0x00 0x01 
	
08:32:13 PM	#20 CDR -400 File Writer.cpp, Line 299
	Unspecified target error
	QSI DVD+-RW SDW-082 (H:1 T:0)
	
08:32:13 PM	#21 Text 0 File DVDR.cpp, Line 3709
	EndDAO: Last written address was 968767 (EC83Fh)
	
08:32:14 PM	#22 Phase 38 File ExtendedProgress.cpp, Line 537
	Burn process failed at 4x (5540 KB/s)


xcdroast 0.98alpha15: DVD-R

Calling: /usr/lib/xcdroast/bin/xcdrwrap CDRECORDDVD dev= "1,0,0" gracetime=10 fs=4096k driveropts=burnfree -v -useinfo speed=4 -dao -eject -pad -data "/*/*.iso" ...

scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
TOC Type: 1 = CD-ROM
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
Driveropts: 'burnfree'
communication breaks or freezes immediately after that.
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   :
Vendor_info    : 'QSI     '
Identification : 'DVD+-RW SDW-082 '
Revision       : 'LX51'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0011 (DVD-R sequential recording)
Profile: 0x002B (DVD+R/DL)
Profile: 0x001B (DVD+R)
Profile: 0x001A (DVD+RW)
Profile: 0x0014 (DVD-RW sequential recording)
Profile: 0x0013 (DVD-RW restricted overwrite)
Profile: 0x0011 (DVD-R sequential recording) (current)
Profile: 0x0010 (DVD-ROM)
Profile: 0x000A (CD-RW)
Profile: 0x0009 (CD-R)
Profile: 0x0008 (CD-ROM)
Profile: 0x0000 (Reserved/Unknown)
Profile: 0x0000 (Reserved/Unknown)
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE
Supported modes: PACKET SAO
Drive buf size : 688128 = 672 KB
Speed set to 5540 KB/s
FIFO size      : 4194304 = 4096 KB
Track 01: data  2216 MB         padsize:   30 KB
Total size:     2546 MB (252:14.45) = 1135084 sectors
Lout start:     2546 MB (252:16/34) = 1135084 sectors
Current Secsize: 2048
ATIP start of lead in:  -150 (00:00/00)
Disk type:    unknown dye (reserved id code)
Manuf. index: -1
Manufacturer: unknown (not in table)
Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 1163412
Starting to write CD/DVD at speed   4.0 in real SAO mode for single session.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Starting new track at sector: 0
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 06 1B 52 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 47 00 00 00 00 0E 09 0C 00 00 00 01 00 00
Sense Key: 0x7 Data Protect, Segment 11
Sense Code: 0x00 Qual 0x01 (filemark detected) Fru 0x0
Sense flags: Blk 0 (not valid) end of medium 
resid: 63488
cmd finished after 0.638s timeout 200s
wodim: A write error occured.
wodim: Please properly read the error message above.

write track data: error after 819630080 bytes
Writing  time:  286.124s
Average write speed   5.9x.
Min drive buffer fill was 47%
Fixating...
Fixating time:    2.485s

```

---

### Post by bierholen on 2007-05-29
My problem seems to be solved. A kernel update from 2.6.20-15 to 2.6.20-16 changed the burner from /dev/scd0 to /dev/hdc and ever since I can burn again (at least so far).

---

### Post by rem on 2007-05-30
> **bierholen said:**
> My problem seems to be solved. A kernel update from 2.6.20-15 to 2.6.20-16 changed the burner from /dev/scd0 to /dev/hdc and ever since I can burn again (at least so far).

Yes, indeed... this seems to be the fix. I tested it myself too and now I can burn DVDs which I couldn't do prior the Kernel update.

---

### Post by Ferri on 2007-06-03
I'm also having this issue, or a very similar one. However, the kernel upgrade didn't do the trick for me.
I've added my results to the bug in [https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/114122[/HTML]"] https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/114122]("[HTML)
Any ideas?

---

### Post by gmconie on 2007-10-25
I have the same problem. I have a TDK cd and a LG dvd burner. Both do this. Only method to burn CD's is to boot XP and burn from there. both  worked  in dapper.

---

### Post by orengolan on 2007-10-28
I am using ubuntu 7.10 and try to burn data into a DVD-R and get those results:
(btw, I don't see any icon on my desktop when inserting the DVD)

GnomeBaker
media is not recognized as recordable DVD: 0

k3b
please insert an empty or appendable dvd

cd/dvd creator
Insert a rewritable or blank disc

when running this command :
sudo hdparm /dev/hdc

I get:
/dev/hdc: No such file or directory

when running this command:
/usr/lib/nautilus-cd-burner/list_cddrives

I get:

```
gnome-mount 0.6

** (gnome-mount:10888): WARNING **: Drive /dev/scd0 does not contain media.
Drive:
  name:                 DVD Writer 300n
  device:               /dev/scd0
  door:                 open
  type:                 CD-R, CD-RW, DVD+R, DVD+RW, CD, DVD
  is mounted:           FALSE
  max read speed:       7056 KiB/s (CD 47.0x, DVD 5.2x)
  max write speed:      2822 KiB/s (CD 18.8x, DVD 2.0x)
  write speeds:         2822 KiB/s (CD 18.8x, DVD 2.0x)
                        1411 KiB/s (CD 9.4x, DVD 1.0x)
                        706 KiB/s (CD 4.7x, DVD 0.5x)

Media:
  label:                ''
  type:                 Couldn't open media
  is writable:          FALSE
  is appendable:        FALSE
  capacity:             Could not be determined
  size:                 Could not be determined
```

any ideas?

---

