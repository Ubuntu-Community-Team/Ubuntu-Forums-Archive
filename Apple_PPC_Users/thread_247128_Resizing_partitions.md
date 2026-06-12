---
title: "Resizing partitions"
date: 2006-08-30
forum: Apple PPC Users
---

### Post by wheli on 2006-08-30
Hey guys...

I had been searching on this topic for awhile, but hadnt found anyone with definate answers on how to resize your OS X partition without destroying it.


Ok......

1.  Make sure you disable Journaling on your harddrive.
2.  Boot your mac with the Live Drapper CD.
3.  Open up terminal and type in "sudo parted"
4.  Type "print" and make a note of the # of the drive that you want to shrink.
5.  Type "resize (drive #) *startpoint endpoint*"
    for example: ***resize 3 128MB 60GB***
6.  Make sure you set aside enough free space to install Ubuntu
7.  The resize process could take up to 2 hours.
8.  after this, you should have enough free space to choose the option "install Ubuntu in free space" during the installation

I hope this helps.

---

### Post by johnrobert on 2006-09-27
Thanks Wheli,

I had found an extensive thread about using parted on the PPC, but the specific instructions related to Breezy and didn't match the Dapper installation procedure. Your note here got me past the discrepancies and I am now happily writing to you from Ubuntu on my G4 Powerbook.

Thanks again!

---

