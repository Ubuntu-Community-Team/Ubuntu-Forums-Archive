---
title: "DeVeDe HELP!!!"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by borovy3488 on 2007-09-19
OK, so I ran devede's processes and it made an iso image on my desktop.  Now, my only problem is burning that ISO!!!!  I have tried GnomeBaker and the iso burner when you right click on the file.  Each time they ended with an error!  I am dieing I have been waiting for 8 hours for the video conversion, and now its as simple as burning an iso and it wont let me do it!!  Does anyone have a clue on what to do??

---

### Post by Pumalite on 2007-09-19
Install k3b if you don't have it
Tools>Burn CD Image

---

### Post by borovy3488 on 2007-09-19
thanks for the help.  How do install k3b?

---

### Post by Pumalite on 2007-09-19
Synaptic>Search>k3b>install

---

### Post by borovy3488 on 2007-09-19
can i use getdeb?

---

### Post by Pumalite on 2007-09-19
You can use this at the Terminal:

sudo apt-get install k3b

---

### Post by borovy3488 on 2007-09-19
oh my god, i still got an error.  Here's what it said::

System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
HL-DT-ST DVD-RW GWA-4040N 1.02 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

Burned media
-----------------------
DVD-R Sequential

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 2.0x1352KBps.
          0/3155308544 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/3155308544 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/3155308544 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-[ WRITE@LBA=0h failed with SK=3h/ASC=0Ch/ACQ=80h]: Input/output error
:-( write failed: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1540678 -dvd-compat -speed=2 -use-the-force-luke=bufsize:32m 

:::

Input/Output error?  I'm so confused

---

### Post by borovy3488 on 2007-09-19
could it be possible that my drive just isn't writing dvds?  I have tried cd's before, but not dvds.  Cd worked fine, but I tried burning a data dvd just now and it didn't work as well.  Is there anyway to fix this??

---

### Post by mondomunchies on 2008-06-04
I know this is an old thread but I just came across the same problem and somehow got it to work:

Alright this may not help you.  I had the same problem.  Trying to burn the iso with brasero it would "erase dvd" like normal (because i'm using dvd rw) and just as its about to burn it gives me the same error you got.  I did this to fix it (and i dont know how it worked)

Put in a different and blank dvd r or rw, wait for the blank disc to appear on your desktop.  then double click on the iso and burn it.  thats it.

---

### Post by boxercbuk on 2008-06-05
ive used devede several times and when it comes to burning the iso just double on the file in the file browser and then select the right drive and click on the write to disk button

---

### Post by Quintin Riis on 2008-06-05
Possibly a faulty DVD burner.

---

