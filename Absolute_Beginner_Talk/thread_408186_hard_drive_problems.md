---
title: "hard drive problems"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by ace0snipe on 2007-04-13
im running a dual boot system that runs fine, perfect in fact, then i noticed i could fit a hard drive into my diskette slot. 

its a 300GB ide with the jumper removed so that its set to 'single master' on that cable. 

ubuntu doesnt see it at all any where. not under any command line, device manager or disk manager

tho my mobo does see it and the live cd will see two hds that it doesnt recognize. 

windows does see the drive and i used windows to remove the ntfs partition on the drive but to no avail, linux still does not see the drive. 

if any one has any ideas let me know. im wondering if theres a way to manually force linux to recognize the drive at a certain address if it doesnt see one. 

i have 5 hard drives on the same system:

250 gb SATA - P1 55gb ntfs - P2 50gb ext3 - P3 5gb swap - P4 (remainder) unallocated
750 gb SATA2 ntfs
750 gb SATA2 ntfs
750 gb SATA2 ntfs
300 gb IDE (unallocated) (the one linux doesnt see that i want to make ext3)

Thx in advance

---

### Post by devnulljp on 2007-04-13
fdisk to format the drive 
mkfs to make a filesystem on it
then mount it
That should do it.

Do
dmesg | grep hd[a-z]

to see if it sees the drive at all

---

### Post by ace0snipe on 2007-04-13
thx, this is what i got from the command you gave me.

erikk@THE-BOX:~$ dmesg | grep hd[a-z]
[   45.768915] activating NMI Watchdog ... done.
[   45.890716] testing NMI watchdog ... OK.
[   47.416423]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda: DMA, hdb: DMA
[   47.416433]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc: pio, hdd: pio
[   48.153406] hda: HL-DT-STDVD-RAM GSA-H22N, ATAPI CD/DVD-ROM drive
[   48.936938] hdb: HL-DT-ST DVDRAM GSA-H10N, ATAPI CD/DVD-ROM drive
[   49.577043] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   49.583113] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   49.988349] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   49.989769] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   50.021208] SCSI device sdb: 1465149168 512-byte hdwr sectors (750156 MB)
[   50.021239] SCSI device sdb: 1465149168 512-byte hdwr sectors (750156 MB)
[   50.038077] SCSI device sdc: 1465149168 512-byte hdwr sectors (750156 MB)
[   50.038110] SCSI device sdc: 1465149168 512-byte hdwr sectors (750156 MB)
[   50.044971] SCSI device sdd: 1465149168 512-byte hdwr sectors (750156 MB)
[   50.045001] SCSI device sdd: 1465149168 512-byte hdwr sectors (750156 MB)
[   57.926990] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
erikk@THE-BOX:~$

i have the asus P5W DH Deluxe (plz dont dis asus, this board is the bomb) and this is what i got off the site:

Storage/RAID
	
Intel ICH7R South Bridge:
  * 1 x UltraDMA 100/66/33
  * 3 x Serial ATA 3.0Gb/s with Intel® Matrix Storage Technology with RAID 0, 1, 5 support
Jmicron JMB363 controller
  * 1 x UltraDMA 133/100/66
  * 1x Serial SATA 3.0Gb/s
  * 1x External Serial ATA 3.0Gb/s (ASUS SATA-on-the-Go)
  * Support SATA RAID 0, 1 and JBOD (by 1x External SATA & 1x Internal SATA)
Silicon Image 4723 Hardware RAID controller (ASUS EZ-Backup)
  * 2 x Serial ATA 3.0Gb/s with RAID 0, 1 support
  * Support RAID 10 cross Intel® ICH7R and Silicon Image 4723 controller

i guess the bios was busy cuz i got no answer on that last one, i think alc882 is the Jmicron JMB363 controller.

from what i can see the south bridge has my 2 dvd drives my boot drive and 2 of the 750's, the 4723 raid controller has the last 750	

my only comment on this is that it detected the same dirve b4 on a previous installation i had a week ago. b4 i got the 3 750gb drives.

im going to see if theres a driver needed for jmicron controller, but plz if any one has any other ideas let me know. thx a lot

---

