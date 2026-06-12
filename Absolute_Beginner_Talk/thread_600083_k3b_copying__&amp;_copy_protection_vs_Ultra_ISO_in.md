---
title: "k3b copying  &amp; copy protection vs Ultra ISO in Windows"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Dakota42784 on 2007-11-01
I download Games that I burn for Grandkids to play.........Have a Problem in Linux as follows:

Some of the games have 2 CDS
Sometimes the CD1 is listed as 751mb or more,............and we all know that a cd only holds 700 mb.
k3b............Won't copy a cd over 700 mb...........BUT
iF I go to Ultra ISO in windows...........It still shows the bin file as 751 mb but removes copy protection & brings the file size to 653 mb...........and Bingo..........I can make an Image that is 653 mb & then I can Burn it. !!!!!

In k3b.........The Cue file is an Image, already.....Right??...........But I can't copy it in k3b. Because k3b shows over 700 mb.:)

:)I have Libdvdcss2 installed & updated.

If you understand this,    Please Help, Thanks

---

### Post by defrex on 2007-11-01
Honestly, if an image is over 700 megs I would think it a DVD image. Do the CDs work after burning them with the aforementioned windows app?

---

### Post by snkmad on 2007-11-01
Sometimes cd images are over 700mb, but when they are written to the cd, some data dont go along, so it does fit on a 700mb cd.

---

### Post by inversekinetix on 2007-11-01
A 700mb CD contains more than 2 billion (2GB) physical bits;  Most are used for basic modulation and error correction that prevents the slightest scratch or piece of dust from making the data unreadable.  This leaves ~800 MB of logical bits available.  Normal data discs use an a additional layer of error correction across 2k blocks of data, leaving 2048/2352 * 803mb = 700MB of space usable to you.

VCDs, Playstation discs, etc have their own error resistance built in to their data files and don't use the standard 2048/2352 ECC.  Thus they fit 800mb of data, and an image might be 800mb.

There are CD-Rs that hold more than 700mb;  They're not really CDs, they're shiny novelty flying discs that may happen to store data on some drives and be readable on others.  Avoid them. 

Use software that allows overburning

---

### Post by Dakota42784 on 2007-11-01
Yes......The programs & cds work correctly after burning with Ultra ISO in Windows.

Ultra ISO..........Removes the Copy Protection & allows burning.........

How do I remove the Copy Protection in k3b & allow me to burn..is my Question??????

Example:  Bin file = 751 MB  so k3b won't allow burning

Ultra ISO sees it as 654 MB     (same file)   and allows burning after creating image:)

---

### Post by snkmad on 2007-11-04
You can try to burn it with Ultra ISO under wine.
I havent burned anythign with it, but creating and modifying isos works just fine.
Heres the info about Ultra ISO on wine: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1650](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1650)

---

