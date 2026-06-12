---
title: "Install help."
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by gt401967 on 2006-08-04
I'm trying to install ubuntu as a second boot (dual boot). Problem is when I try to load the startup gets hung trying to load the root file system???
I've tried using both the 64bit disk and the regular disk, and get the same result.

hda: cdrom_pc_intr: The drive appears confused (ireason = 0X01)

System Specs:

Processor 
Pentium D 805
2700 megahertz Intel Pentium 4 (2 installed)
32 kilobyte primary memory cache
1024 kilobyte secondary memory cache

Board: ASUSTeK Computer INC. P5WD2-Premium Rev 1.xx
Bus Clock: 133 megahertz
BIOS: American Megatrends Inc. 0709 03/31/2006

Memory
2048 Megabytes Installed Memory

Drives
820.16 Gigabytes Usable Hard Drive Capacity
465.10 Gigabytes Hard Drive Free Space

SONY CD-RW CRX320E [CD-ROM drive]
SONY DVD RW DW-Q120A [CD-ROM drive]
3.5" format removeable media [Floppy drive]

ST3120026A [Hard drive] (120.03 GB) -- drive 1
ST3300822AS [Hard drive] (300.07 GB) -- drive 0
ST3400832A [Hard drive] (137.44 GB) -- drive 2

---

### Post by nalmeth on 2006-08-04
```
 hda: cdrom_pc_intr: The drive appears confused (ireason = 0X01)
``` Is that really the output? Funny, never seen that one before. Perhaps you have a corrupted image or burn.
Did you order the CD's? Or burn them? If you burned them, did you do an md5sum check to test their integrity? How fast did you burn the discs at? The slower the better.

---

### Post by gt401967 on 2006-08-04
That is truly the output, except there is a timer right before the code.  I get it with both the regular and 64 bit versions.  The only difference is the the regular version starts it's clock at something much higher than the 64 bit.  I have checked the images, and both are not corrupt.  I burnd the disks at 40x.  I'll try something slower.
Any ideas?

---

### Post by gt401967 on 2006-08-04
Burned again at 16x.  It still gets hung during the "Mounting root file system".  Not exactly sure where the issue is...I have 3 harddrives installed.

300gb Sata drive
30gb partition ntfs -primary windows
20gb partition fat32 -Where I want to install ubuntu
rest is ntfs

400gb ntfs

160gb 
10gb partition ntfs
5gb partition ntfs
145 partition ntfs

Is it a problem with the hardware setup?

---

### Post by hazash on 2006-08-04
For me it too quite a while before the root system was loaded, try to wait like 10 min or so..

---

### Post by richbarna on 2006-08-04
Better still, burn at 4-8X if you can, also use good CD's I ahve never had a problem with Verbatim discs on an 8X burn.

---

### Post by mgist007 on 2006-08-27
I have the same problem with almost the same setup as you do.  I even tried to load version 5 and it stops at detecting the cd rom.  That is the problem but I have not figured how to fix it yet If anyone Else knows we would appreciate it.

---

### Post by mgist007 on 2006-08-27
Found answer to your problem.  When using  version 6 when the menu comes up press f6 and add a space and then irqpoll to the command line then enter will work fine.

---

