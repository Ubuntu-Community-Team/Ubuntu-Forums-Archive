---
title: "Can't burn DVD+R"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by motion parallax on 2008-02-05
I can burn DVD+ and - R in Windows, but only DVD-R in ubuntu.  I've tried three different burning programs, all with the same results.

All my google searches bring up the reverse of this problem.    

Is there any way to burn DVD+Rs in Ubuntu?

---

### Post by emarkd on 2008-02-05
Do you get an error message that may be helpful?  I have no problem burning +R disks with my burner.

---

### Post by motion parallax on 2008-02-05
I'll have to try burning another disk.  Post in a few minutes.

---

### Post by motion parallax on 2008-02-05
Debugging output from KDE

System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
Slimtype DVDRW SSM-8515S GRS6 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD+R

K3bIsoImager
-----------------------
mkisofs print size result: 268791 (550483968 bytes)
Pipe throughput: 17300480 bytes read, 17299456 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
growisofs: 7.0.1

---

### Post by motion parallax on 2008-02-05
Can't post the rest of this debug.  The forum keeps giving me an error saying I have too many images in the post, which is weird since I didn't put ANY images in it.

---

### Post by %hMa@?b&lt;C on 2008-02-05
save it to a text file and attach it. or put it on pastebin so that I can look at it.

---

### Post by motion parallax on 2008-02-05
Bottom of the debugging info:  

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid Family Guy - S06E01-02 (5ACX16-2 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-mer/k3bUYj9jb.tmp -rational-rock -hide-list /tmp/kde-mer/k3b42Plvb.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-mer/k3bN2m8za.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-mer/k3bs2Ijaa.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid Family Guy - S06E01-02 (5ACX16-2 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-mer/k3bHzBl8b.tmp -rational-rock -hide-list /tmp/kde-mer/k3bGTIKsa.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-mer/k3bksaKvb.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-mer/k3bXYmTva.tmp

---

### Post by motion parallax on 2008-02-05
Does this work?

---

### Post by motion parallax on 2008-02-06
Bump.

---

### Post by mc4man on 2008-02-06
i don't use any of those apps for dvd build/burn operations so I'm unfamiliar with the log output/errors. I'm assuming your app(s) are doing an iso build then burn or a build, burn on the fly. Is there any way to post the exact size of the iso to be burned and or the size of the source your building from ? (in bytes)

---

### Post by Shadowmeph on 2008-02-06
funny thing with me I was trying to burn something and it wouldn't work on my first burner but the other burner I have installed it did work so in windows language ( the only language I know right now ) it would be drive D which is my first dvd burner it doesn't work but if I put the dvdr into drive E it works from there which doesn't make sense to me if I where in windows I would just change the drive letters around but this is linux which is totaly different

---

### Post by motion parallax on 2008-02-06
I've tried to burn files of every shape and size.  Mainly AVI.  I've set up burns to fill the entire disc ~ 4.2GB or so, as well as burns of under 1GB just to test.  

I've tried data and iso burns.  Neither work.  

These same burns work with DVD-R.  I tried burning a 4GB DVD of AVI files on a DVD+R didn't work, so I tried the same files on a DVD-R and it worked.

---

### Post by motion parallax on 2008-02-07
Bump

---

