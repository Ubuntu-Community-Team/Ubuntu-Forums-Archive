---
title: "Livecd Help"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-01-07
hi, i'm a total noob at this, so bear with me. i eventually plan to ditch windows for linux, since i'm sick of their crap & WILL NOT BUY VISTA!!!!

today i burnt a livecd with the infrarecorder thing @ default settings, and put it in, but i got this errors about x not working. i ended up at the command line next & im like wtf lol.. i turned off comp & now back @ windows. do i have to burn it @ 4x speed for this to work? or is the problem w/ my display? here's some system info provided by belarc advisor, if u need anymore, let me know.

note that i don't want to install yet, just try the live cd. when i do decide to install, i'll get rid of windows.  :P

+++

MAIN CIRCUIT BOARD

Board: Intel Corporation D945GNT AAC96324-401
Serial Number: AZNT55202512
Bus Clock: 200 megahertz
BIOS: Intel Corp. NT94510J.86A.3239.2005.1205.1900 12/05/2005

PROCESSOR

3.00 gigahertz Intel Pentium 4
16 kilobyte primary memory cache
2048 kilobyte secondary memory cache

MEMORY MODULES

1024 Megabytes Installed Memory

Slot 'J6H1' has 512 MB (serial number 0xB51272C4)
Slot 'J6H2' is Empty
Slot 'J6J1' has 512 MB (serial number 0xB41215C5)
Slot 'J6J2' is Empty

DRIVES

80.02 Gigabytes Usable Hard Drive Capacity
60.18 Gigabytes Hard Drive Free Space

AXV CD/DVD-ROM SCSI CdRom Device [CD-ROM drive]
LITE-ON DVDRW SHW-160P6S [CD-ROM drive]
3.5" format removeable media [Floppy drive]

WDC WD800JD-60LSA0 [Hard drive] (80.02 GB) -- drive 0

CONTROLLERS

Standard floppy disk controller
Intel(R) 82801G (ICH7 Family) Ultra ATA Storage Controllers - 27DF
Intel(R) 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller - 27C0
Primary IDE Channel [Controller] (2x)
Secondary IDE Channel [Controller]

DISPLAY

RADEON X800 Series [Display adapter]
RADEON X800 Series - Secondary [Display adapter]
AOC LM942 [Monitor] (19.1"vis, s/n T9HJ5CAN00126, December 2005)

---

### Post by justifier on 2007-01-07
try taking your secondry moniter card out, it may be confuseing X

---

### Post by lunaz on 2007-01-07
hm, whats that? lol.. i'm not too great at the whole opening case/messing with things..things. i had this comp built for me by a local company.

---

### Post by houstonbofh on 2007-01-07
You have two video cards, and they also happen to be cards with some of the worst Linux support around.  Hopefully since AMD bought them, this will change, but for now you are stuck.  To make it work, you will need to configure X with dual video card support from the command line and restart X from the live CD to make it work.  This is not simple.  You might want to try the Linux Mint [http://lt.k1011.nutime.de/](http://lt.k1011.nutime.de/) live cd, which is Ubuntu with some of those things done for you.  However, it is enough different that you may have support issues here.

Also, put your location in your profile.  Someone may be local who can help a lot more.

---

### Post by lunaz on 2007-01-27
hm, ty for the replies, sorry it took so long to get back, no time lately ;(

can i disable radeon x800 series - secondary from the device manager in windows to make this work? or is there something in bios i can do? also, what about onboard video? some guy who works at best buy uses linux some, and he told me that would do it, don't even remember his name haha, can't find many local ppl to learn this with. :( not gonna give up tho, i really want to. will even try out other distros. just neeed more time in a day. :P

---

### Post by houstonbofh on 2007-01-30
> **lunaz said:**
> hm, ty for the replies, sorry it took so long to get back, no time lately ;(

can i disable radeon x800 series - secondary from the device manager in windows to make this work? or is there something in bios i can do? also, what about onboard video? some guy who works at best buy uses linux some, and he told me that would do it, don't even remember his name haha, can't find many local ppl to learn this with. :( not gonna give up tho, i really want to. will even try out other distros. just neeed more time in a day. :P
No configuration in Windows will affect Ubuntu.  Again, I would try Linux Mint.  It is Ubuntu with all the hard stuff for you video card done for you.

---

