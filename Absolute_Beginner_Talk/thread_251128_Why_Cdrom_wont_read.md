---
title: "Why Cdrom wont read"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by dombev on 2006-09-05
Just install Ubuntu via Parallels on a MacBookPro. Everything work fine(What a great distro!).
Only one problem the cdrom drive is mounted(Places/computer I can see the cdrom drive) when I insert a cd, the cd icon is displayed on the desktop, I click "open" and see a blank cd!!

Help on this matter will be greatly appreciate

Dombev

---

### Post by jorn on 2006-09-05
I assume you have tried different cd's or the ubuntu cd.

---

### Post by dombev on 2006-09-05
Yes, I have and here is my fstab:

/dev/hdb /media/cdrom0 auto udf,iso9660 user,noauto 0 0

This drive me crazy

Any help

---

### Post by dombev on 2006-09-06
I still donnt find a solution 
please help

---

### Post by dombev on 2006-09-12
Please, please, help I try everything and still the same problem

---

### Post by DW5 on 2006-09-15
My drive just started doing this, too. It had been working fine, but now while it is mounted and visible to nautilus, it shows no files (both music cds, and video dvds).  My computer is a compaq nx9010 laptop.

FSTAB says: /dev/hdc /media/cdrom0  udf,iso9660 user,noauto  0   0

but again, it had been working up until recently.  The only thing I've done is install xubuntu.  I noticed it didn't work there, and so switched back into gnome and it doesn't work there either.

DMESG output relevant to this drive is:

```
[17179984.804000] hdc: packet command error: status=0x51 { DriveReady SeekComple te Error }
[17179984.804000] hdc: packet command error: error=0x34 { AbortedCommand LastFai ledSense=0x03 }
[17179984.804000] ide: failed opcode was: unknown
[17179984.804000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[17179984.828000] hdc: packet command error: status=0x51 { DriveReady SeekComple te Error }
[17179984.828000] hdc: packet command error: error=0x34 { AbortedCommand LastFai ledSense=0x03 }
[17179984.828000] ide: failed opcode was: unknown
[17179984.832000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[17179984.840000] hdc: packet command error: status=0x51 { DriveReady SeekComple te Error }
[17179984.840000] hdc: packet command error: error=0x34 { AbortedCommand LastFai ledSense=0x03 }
[17179984.840000] ide: failed opcode was: unknown
[17179984.840000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[17179984.840000] cdrom: This disc doesn't have any tracks I recognize!
[17179984.844000] hdc: packet command error: status=0x51 { DriveReady SeekComple te Error }
[17179984.844000] hdc: packet command error: error=0x34 { AbortedCommand LastFai ledSense=0x03 }
[17179984.844000] ide: failed opcode was: unknown
[17179984.844000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[17181155.012000] hdc: packet command error: status=0x51 { DriveReady SeekComple te Error }
[17181155.012000] hdc: packet command error: error=0x34 { AbortedCommand LastFai ledSense=0x03 }
[17181155.012000] ide: failed opcode was: unknown
[17181155.012000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[17181155.036000] hdc: packet command error: status=0x51 { DriveReady SeekComple te Error }
[17181155.036000] hdc: packet command error: error=0x34 { AbortedCommand LastFai ledSense=0x03 }
[17181155.036000] ide: failed opcode was: unknown
[17181155.036000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[17181155.044000] hdc: packet command error: status=0x51 { DriveReady SeekComple te Error }
[17181155.044000] hdc: packet command error: error=0x34 { AbortedCommand LastFai ledSense=0x03 }
[17181155.044000] ide: failed opcode was: unknown
[17181155.044000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[17181155.048000] cdrom: This disc doesn't have any tracks I recognize!
[17181155.052000] hdc: packet command error: status=0x51 { DriveReady SeekComple te Error }
[17181155.052000] hdc: packet command error: error=0x34 { AbortedCommand LastFai ledSense=0x03 }
[17181155.052000] ide: failed opcode was: unknown
[17181155.052000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00

```

DW

---

### Post by Najand on 2006-09-15
Can you guys run this command in the terminal and copy and paste the ouput here:
```
sudo fdisk -l
```

---

### Post by DW5 on 2006-09-15
When I run fdisk -l I get

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2812    22587358+  83  Linux
/dev/hda2            2813        9729    55560802+   5  Extended
/dev/hda5            9376        9729     2843473+  82  Linux swap / Solaris
/dev/hda6            2813        9375    52717234+  83  Linux

Partition table entries are not in disk order

```

---

### Post by Najand on 2006-09-15
Well, please put some media in your CD-ROM Drive and do it again.

---

### Post by DW5 on 2006-09-15
It has media in it.  In fact I've done fdisk -l with three different cds in it.  Results are the same.

---

### Post by Najand on 2006-09-15
Seems like your CD device file (/dev/hdc/ has been broken... It is a kernel problem... Do you still have old kernels installed? if so is  it possible to boot it again with one of the old ones?

---

### Post by DW5 on 2006-09-15
In the meantime I have been searching in the old forums and found this:

[http://ubuntuforums.org/archive/index.php/t-2345.html](http://ubuntuforums.org/archive/index.php/t-2345.html)

it recommended disabling DMA on the CD-ROM drive using:

```
echo 'using_dma:0' | sudo tee /proc/ide/hdc/settings
```

that worked... I can now read all those disks, but the dvd playback is really choppy using Totem.

I'll reboot into an old kernel and see what happens after lunch.

Thanks for the assistance.

DW

---

