---
title: "Problems With Erasing Dvdrw"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Urko on 2007-11-01
Hello

I' am using Gutsy and last time I tried to erase DVDrw disc. If I use command:
* dvdrecord blank=all dev=/dev/dvdrw, it gives me following error:

Starting to write CD/DVD at speed 1 in write mode for single session.
Last chance to quit, starting real write in 0 seconds. Operation starts.
dvdrecord: Input/output error. blank unit: scsi sendcmd: no error
CDB:  A1 00 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 9600s
dvdrecord: Cannot blank disk, aborting.

Than I tried to use other command (dvd+rw-format -blank /dev/cdrw), but system gives me another error:

* BD/DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
* 4.7GB DVD+RW media detected.
- illegal command-line option for this media.
- you have the option to re-run dvd+rw-format with:
  -lead-out  to elicit lead-out relocation for better
             DVD-ROM compatibility, data is not affected;
  -force     to enforce new format (not recommended)
             and wipe the data.

Then I sad, ok I wil trie force command. But after formating, system couldn't mount disc. (gives an error)

Later I tried earse dvdrw with k3b or gnomebaker. Same story :( . After a second of earisng programs eject dvdrw like it is well done formated, but when I manualy look if it is realy formated,files are still on disc. I even tried overburn files, but no succes :(

If I erase cdrw disc with (cdrecord blank=all dev=/dev/cdrw) command it works fine with no problems.

I don't wanna use Nerolinux becouse is nonfree, I prefer erasing disc in command line. What can I do to erase dvdrw with no problems?

Thnx

---

### Post by damotor on 2007-11-01
Have you tried > dvd+rw-format -force /dev/dvd ?

---

### Post by Urko on 2007-11-01
If I tried commad you write me, it gives me the same error after formating :

invalid mount option when attempting to mount the volume.

Than I can't use dvdrw disc again, unless I erase it on my friend's windows with nero. But I don't want to use windows so now I don't know why ysystem don't want normaly erase dvd :(

---

### Post by Urko on 2007-11-01
Here are my dvdrecorder info :

INQUIRY:                [_NEC    ][DVD_RW ND-3540A ][1.04]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         1Ah, DVD+RW
 Media ID:              RICOHJPN/W11
 Current Write Speed:   1.0x1385=1411KB/s
 Write Speed #0:        6.1x1385=8467KB/s
 Write Speed #1:        5.1x1385=7056KB/s
 Write Speed #2:        4.1x1385=5645KB/s
 Write Speed #3:        3.1x1385=4234KB/s
 Write Speed #4:        2.0x1385=2822KB/s
 Write Speed #5:        1.0x1385=1411KB/s
GET [CURRENT] PERFORMANCE:
 Write Performance:     2.4x1385=3324KB/s@[0 -> 2295104]
 Speed Descriptor#0:    00/2295104 R@5.0x1385=6925KB/s W@4.0x1385=5540KB/s
 Speed Descriptor#1:    00/2295104 R@5.0x1385=6925KB/s W@2.4x1385=3324KB/s
READ DVD STRUCTURE[#0h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    2295104*2KB=4700372992
READ DISC INFORMATION:
 Disc status:           complete
 Number of Sessions:    1
 State of Last Session: complete
 Number of Tracks:      1
 BG Format Status:      suspended
READ FORMAT CAPACITIES:
 formatted:             2295104*2048=4700372992
 26h(0):                2295104*2048=4700372992
READ TRACK INFORMATION[#1]:
 Track State:           complete
 Track Start Address:   0*2KB
 Free Blocks:           0*2KB
 Track Size:            2295104*2KB
FABRICATED TOC:
 Track#1  :             14@0
 Track#AA :             14@2295104
 Multi-session Info:    #1@0
READ CAPACITY:          2295104*2048=4700372992

---

