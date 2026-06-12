---
title: "DVD copy verification"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by Astrikor on 2007-08-03
I am using DVD Copy from the right-click menu on my inserted dvd icon and if works fine (my own dvd made from camcorder).
BUT there is no verification option.  Is this as issue ??

(Note: I have tried K3b (which does have a verification option), but it reports a write error before anything happens.)

Any advice would be helpful!
Thanks

---

### Post by apswartz on 2007-08-03
I use k3b for the verification. What is the error you are getting?

---

### Post by Astrikor on 2007-08-03
Hi Apswartz

I just get a write error message before initial copy even starts. I have reproduced the log below.
[B]Any help appreciated, but that is not really my point.  I am querying the value of the validation process - if validation is important (as I had previously assumed it was - to confirm data integrity) then why is it not available on the standard Ubuntu dvd copy function?

Any comments???[/B]

Log is as follows:

System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
PIONEER DVD-RW  DVR-108 1.19 (/dev/hdd, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

PIONEER DVD-ROM DVD-106 1.22 (/dev/hdc, ) [CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM] [None]
Burned media
-----------------------
DVD-R Sequential

K3bDataTrackReader
-----------------------
reading sectors 0 to 0 with sector size 2048. Length: 1 sectors, 2048 bytes.
using buffer size of 64 blocks.
Read a total of 1 sectors (2048 bytes)

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hdd obs=32k seek=0'
:-( write failed: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/hdd=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1 -dvd-compat -speed=8 -use-the-force-luke=bufsize:32m 

end of log.

---

### Post by apswartz on 2007-08-03
Sadly, this seems to be a known bug...
[https://bugs.launchpad.net/ubuntu/+source/cdrtools/+bug/15424](https://bugs.launchpad.net/ubuntu/+source/cdrtools/+bug/15424)

Since you have another way to burn the DVDs you aren't so bad off :-)

---

### Post by Astrikor on 2007-08-04
> **apswartz said:**
> Sadly, this seems to be a known bug...
[https://bugs.launchpad.net/ubuntu/+source/cdrtools/+bug/15424](https://bugs.launchpad.net/ubuntu/+source/cdrtools/+bug/15424)

Since you have another way to burn the DVDs you aren't so bad off :-)
  True, but how do I know if the dvd copy is corrupted if I can't run a verification check?

---

### Post by apswartz on 2007-08-04
See if this article is of any help in verifying your DVDs...
[http://www.g-loaded.eu/2006/10/07/verify-a-burned-cddvd-image-on-linux/](http://www.g-loaded.eu/2006/10/07/verify-a-burned-cddvd-image-on-linux/)

---

### Post by Astrikor on 2007-08-05
> **apswartz said:**
> See if this article is of any help in verifying your DVDs...
[http://www.g-loaded.eu/2006/10/07/verify-a-burned-cddvd-image-on-linux/](http://www.g-loaded.eu/2006/10/07/verify-a-burned-cddvd-image-on-linux/)


Many thanks Apswartz - a very useful link which offers several solutions.
Astrikor   :)

---

