---
title: "K3B help wont burn dvd iso"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by jza873 on 2008-03-17
i also posted this on kubuntu forums but this community is much better.  and yes i am a kde / flux user.  thanks in advance

got an ISO and i try to burn it so i can watch it on my dvd player this was working up until yesterday no new updates i tried to remove k3b and reinstall it i also removed my ~/.kde/ folder so it went back to default and i'm still getting this problem where it says

X flushing cache this may take some time  (then it says)
X Write error
and then it closes the dvd so its useless  her is the log

BTW i had Sony dvd's and they didn't work at all and i bought Imation ones and it worked once yesterday and now it don't work any more.  any help would be appreciated.


System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
MATSHITA DVD-RAM UJ-85JS F100 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD+R

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 2.5x1352KBps.
    1572864/2264414208 ( 0.1%) @0.0x, remaining 191:49 RBU 100.0% UBU   2.1%
    1572864/2264414208 ( 0.1%) @0.0x, remaining 287:44 RBU 100.0% UBU 100.0%
    1572864/2264414208 ( 0.1%) @0.0x, remaining 359:40 RBU 100.0% UBU 100.0%
    1572864/2264414208 ( 0.1%) @0.0x, remaining 431:36 RBU 100.0% UBU 100.0%
    1572864/2264414208 ( 0.1%) @0.0x, remaining 527:30 RBU 100.0% UBU 100.0%
    1572864/2264414208 ( 0.1%) @0.0x, remaining 599:26 RBU 100.0% UBU 100.0%
    2392064/2264414208 ( 0.1%) @0.2x, remaining 441:17 RBU 100.0% UBU  93.8%
    3112960/2264414208 ( 0.1%) @0.2x, remaining 387:25 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=5f0h failed with SK=4h/ASC=03h/ACQ=00h]: Input/output error
:-( write failed: Input/output error
/dev/scd0: flushing cache
/dev/scd0: closing track
/dev/scd0: closing disc

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1105671 -dvd-compat -speed=2.4 -overburn -use-the-force-luke=bufsize:32m

---

### Post by dca on 2008-03-17
[http://www.linuxquestions.org/questions/linux-hardware-18/dvd-burn-failure-196242/](http://www.linuxquestions.org/questions/linux-hardware-18/dvd-burn-failure-196242/)
 
See if the above post is similar to the issue(s) you're experiencing...

---

### Post by jza873 on 2008-03-17
no not same issue his will burn some of the way.  mine will stay at 0% and then say closing disk and then the dvd is useless.  i been messing with it for like 9 hours and i cant figure it out it worked last night.  after i burned an iso the movie played fine and then i couldn't do it again i thought maybe kde was eating up too much cache so tried in flux and same thing.  i think the problem is the cache file from buring like 40 dvd's  in the past 2 weeks made it go crazy.  the thing is i have no idea where cache for k3b is held or even cache for the file system.  been googleing like crazy and no answer.  but his is almost the same as mine.  but his will write a little and not work my dont work at all.  i can burn data cd's  and audio cd's.  but once i try to do it with a dvd it dotn work and i tried imation + and -  R ones and both failed so no data dvd and no video dvd.  i just tried to creat a data dvd and it has all teh files on it but there blank like 30000 pictures and no images are displayed.  bout to reload kubuntu again or go back with arch or fluxbuntu.

---

### Post by MonctonJohn on 2008-03-17
Did you rule out a hardware problem?

Try booting with a live CD and try out burning. If that doesn't work you may have a harware issue.

---

### Post by disturbedite on 2008-03-17
i have the same problem, dvds won't burn but cds will.
i think i know what the problem is.  i think with a recent kernel update (2.6.24-x) that recorders were renamed to /dev/sr0 or something like that.
so when you try to burn with your old scd0 it fails to find the device. more specifically, i think this is creating a problem with growisofs not finding the device.
i am, however, able to burn dvds with gnomebaker.

---

### Post by jza873 on 2008-03-17
ok i found the issue in controlcenter -->KDE Components --> Service Manager i click on it and get "Unable to contact "KDED"  no media manager running cant load flash or firewire its odd i ont knw how this happened i burned a dvd last night turned off my computer turned it back on didnt install anything or remove anything and got all these issues OH MY GOD ITS BECOMING WINDOWS (jk)  nothing is that bad

well i killed my dcopserver and rebooted the computer i can mount volumes again but still no luck on the dvd burning imma try gnomebaker and see if that works  but it also failed its still outputting the iso to /dev/sdc0/

---

