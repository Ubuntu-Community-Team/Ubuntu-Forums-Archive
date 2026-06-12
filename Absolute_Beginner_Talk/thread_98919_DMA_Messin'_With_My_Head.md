---
title: "DMA Messin' With My Head"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by linewb on 2005-12-04
I know there's many posts on DMA for DVD playback, but I'm still having trouble with an external rewriter connected to a USB port.  It play choppy and skips.  It read in Device Manager as /dev/scd0.  Here's what I've got:

> ~$ sudo hdparm -d1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Invalid argument


This didn't solve the problem.  It was still playing choppy.  So I tried to take a look at my settings:

> ~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Not sure what the problem could be?  Am I reading the drive wrong as scd0?  Any suggestions are greatly appreciated.

Rewriter is LG 16x External Super Multi DVD/CD Rewrier GSA-2166D.  Hard drive is AMD Athlon 1600+.

---

### Post by monkeyface on 2005-12-04
I don't think that you can set DMA for SCSI/SATA/USB devices.
I'm getting the same error message when trying to enable DMA for my SATA drives and USB harddisk.

---

### Post by linewb on 2005-12-05
Hmmm.  I see.  Thanks for the info.  If I can't set DMA for that device, then does anyone know what can I do to fix the choppy play?

---

