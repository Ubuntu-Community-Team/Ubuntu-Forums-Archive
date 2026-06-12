---
title: "Magneto Optical drives?"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by sfpeter on 2006-06-05
I have two magneto optical drives in my computer, a 640MB IDE 3.5 inch and a 2.5GB 5.25 inch SCSI.  Both are mounted internally and were working under Windows before I converted over.  I can't see the disks in Places under Computer, and the Device Manager is showing them as unrecognized.  I tried downloading LVM but it didn't make any difference.  Is there a driver or setting or something obvious I'm missing?

---

### Post by mips on 2006-06-05
Brand & model of the drives ?
Brand & model of the scsi card ?

You need to provide more information...

---

### Post by sfpeter on 2006-06-05
Hello:

The 640MB IDE is a Fujitsu Dynamo.

The SCSI is an HP c1113F on an Adaptec AHA-2940UW.

---

### Post by sfpeter on 2006-06-05
Here's what I get when I grep the SCSI card:

itsme2@itsme2:~$ dmesg | grep sdb
[4294691.759000] SCSI device sdb: 1273011 1024-byte hdwr sectors (1304 MB)
[4294691.760000] sdb: Write Protect is off
[4294691.760000] sdb: Mode Sense: 37 03 10 08
[4294691.761000] SCSI device sdb: drive cache: write through
[4294691.763000] SCSI device sdb: 1273011 1024-byte hdwr sectors (1304 MB)
[4294691.764000] sdb: Write Protect is off
[4294691.764000] sdb: Mode Sense: 37 03 10 08
[4294691.766000] SCSI device sdb: drive cache: write through
[4294691.766000]  sdb: sdb1
[4294691.792000] sd 2:0:0:0: Attached scsi removable disk sdb
[4294695.505000] Buffer I/O error on device sdb1, logical block 2538112
[4294695.505000] Buffer I/O error on device sdb1, logical block 2538113
[4294695.505000] Buffer I/O error on device sdb1, logical block 2538114
[4294695.505000] Buffer I/O error on device sdb1, logical block 2538115
[4294695.505000] Buffer I/O error on device sdb1, logical block 2538112
[4294695.505000] Buffer I/O error on device sdb1, logical block 2538113
[4294695.505000] Buffer I/O error on device sdb1, logical block 2538114
[4294695.505000] Buffer I/O error on device sdb1, logical block 2538115
[4294695.505000] Buffer I/O error on device sdb1, logical block 2538204
[4294695.505000] Buffer I/O error on device sdb1, logical block 2538205
[4294704.170000] Buffer I/O error on device sdb1, logical block 2538112
[4294708.584000] Buffer I/O error on device sdb1, logical block 2538112

(I put in an unformatted disk until I can straighten this out)

What does this mean?  It's recognizing SDA as my Serial ATA drive controller, so do I need to add this drive to fstab?  If so, how do I do that?

---

### Post by sfpeter on 2006-06-05
Here's the output of:

sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29644   238115398+  83  Linux
/dev/sda2           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris
Note: sector size is 1024 (not 512)

Disk /dev/sdb: 1303 MB, 1303563264 bytes
255 heads, 63 sectors/track, 79 cylinders
Units = cylinders of 16065 * 1024 = 16450560 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         158     2538207    b  W95 FAT32

and this one:

cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0     


and lastly this:

df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             224G  3.2G  210G   2% /
varrun               1014M   80K 1014M   1% /var/run
varlock              1014M  4.0K 1014M   1% /var/lock
udev                 1014M  180K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   19M  996M   2% /lib/modules/2.6.15-23-386/volatile

Any ideas what I need to do?

---

### Post by sfpeter on 2006-06-05
I've made a little progress on the SCSI drive:

I figured out how to edit fstab, and made the following entry:

0       0
/dev/sdb1	/mnt/optic1	vfat, user

I also defined a mountpoint /mnt/optic1.  Gparted sees the SCSI drive, and I can get the disk mounter to make an icon for it.  I put in a disk formatted to fat32, but the disk mounter says unrecognized file type, and Gparted crashes with an error when I try to format it.  Help?

---

### Post by sfpeter on 2006-06-05
Last try before I wait for a reply:

dmesg | grep hd

shows me this:

[4294671.214000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[4294671.214000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[4294671.228000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[4294671.230000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[4294672.405000] hdc: HL-DT-ST DVDRAM GSA-4165B, ATAPI CD/DVD-ROM drive
[4294672.813000] hdd: FUJITSU MCF3064AP, ATAPI OPTICAL drive
[4294672.880000] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294672.888000] hdd: ATAPI magneto-optical drive
[4294705.440000] hdd: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4294705.440000] hdd: packet command error: error=0x50 { LastFailedSense=0x05 }
[4294705.769000] hdd: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4294705.769000] hdd: packet command error: error=0x50 { LastFailedSense=0x05 }
[4295250.146000] SCSI device sdb: 1273011 1024-byte hdwr sectors (1304 MB)
[4295250.150000] SCSI device sdb: 1273011 1024-byte hdwr sectors (1304 MB)
[4295250.743000] hdd: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295250.743000] hdd: packet command error: error=0x50 { LastFailedSense=0x05 }
[4295250.750000] hdd: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295250.750000] hdd: packet command error: error=0x50 { LastFailedSense=0x05 }

---

### Post by sfpeter on 2006-06-05
Well, one more thing, here what I can find on the IDE drive:  

/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

 Model=FUJITSU MCF3064AP, FwRev=0032, SerialNo=00S3016958200
 Config={ Fixed Removeable DTR<=5Mbs DTR>5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:383,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 *mdma2
 AdvancedPM=no WriteCache=disabled
 Drive conforms to: Unspecified:  ATA/ATAPI-4

 * signifies the current active mode

---

### Post by sfpeter on 2006-06-05
Okay, I think I figured it out.

My SCSI drive was SDB one and the disk I was using had a bad side.  (extremely rare with these discs but it happens).  Format a good disk to Fat 32 and it works.

The IDE was HDD, and the same deal, has to be Fat 32.  

For future reference, here's my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb	/mnt/optic1	vfat	noauto,rw,user
0       0
/dev/hdd	/mnt/optic2	vfat	noauto,rw,user

And here's some pictures of cute kittens:

[http://www.petebevin.com/kittens/](http://www.petebevin.com/kittens/)

Enjoy.

---

