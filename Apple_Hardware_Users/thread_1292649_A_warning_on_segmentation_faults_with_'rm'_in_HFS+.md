---
title: "A warning on segmentation faults with 'rm' in HFS+"
date: 2009-10-16
forum: Apple Hardware Users
---

### Post by led_belly on 2009-10-16
Hello,

I have found that when performing 'rm -fr' in Ubuntu on an hfsplus (non-journaled) formatted filesystem directory containing a large amount of files (100+ gigs), I often encounter a segmentation fault which is unrecoverable (i.e.: leads to dead processes, drive becomes unmountable). My only option to gain access again to the drive is to restart which always leads to corruption of the data on the drive (due to journalling being not available). fsck.hfsplus cannot repair the drive, nor can Disk Utility in Mac OS X. On these occasions I have had to reformat the drive and restore from backup.

I don't know why this happens... just an FYI and if anyone out there can offer a suggestion it would be helpful.

Cheers

---

