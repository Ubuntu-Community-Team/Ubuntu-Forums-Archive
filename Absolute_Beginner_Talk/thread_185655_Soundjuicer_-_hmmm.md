---
title: "Soundjuicer - hmmm"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by millsy on 2006-06-01
Hi - I'm pretty new to linux but I've followed all the instructions on how to set up soundjuicer to rip cd's to mp3 format.

The problem is that soundjuicer doesn't see my CD ROM drive.  Every other multimedia application i have installed (grip, cd player, totem) can read and play the audio cd in the drive but soundjuicer doesn't even attempt to read it.

I imagine that this is a simple thing to fix but I'm stumped!  The only thing I can think is that the CD Drive option under preferences shows 'CD-224E' rather than /dev/hdd.  Or, the 'device' in the configuration editor for soundjuicer shows '<no value>.

I presume that I shouldn't be able to read the audio CD in nautilus?  When I double click on CD ROM 1 it gives me this message ...

  mount: block device /dev/hdd is write-protected, mounting read-only
  mount: wrong fs type, bad option, bad superblock on /dev/hdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

At the moment, I'm ripping on a windows machine and transferring the mp3s manually to my ubuntu box.  I'd love to get this working - please help!!

Mark

---

### Post by smsmith050 on 2006-06-02
Soundjuicer works for me but it is soooo slow. The first time I used it the extract speed was 10x. Next time - same CD - samd drive 1.5x. I would say you are better off not using Soundjuicer. 
There are some pretty smart ubuntu users here that might be able to help you if they had more info. 
post some of your system info, the output from the following commands.

cat /var/log/messages |grep CD (to find your CD) 

hdparm -i /dev/hdc (hdc or what ever your drive is) 
/dev/hdc:

 Model=LITE-ON DVDRW SOHW-1693S, FwRev=KS0A, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-5

 * signifies the current active mode

sound-juicer --gst-version
GStreamer Core Library version 0.10.6

uname -a
Linux ubuntu 2.6.15-23-686 #1 SMP PREEMPT Tue May 23 14:03:07 UTC 2006 i686 GNU/Linux

---

