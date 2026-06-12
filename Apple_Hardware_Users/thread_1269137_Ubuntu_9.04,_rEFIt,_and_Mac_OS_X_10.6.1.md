---
title: "Ubuntu 9.04, rEFIt, and Mac OS X 10.6.1"
date: 2009-09-17
forum: Apple Hardware Users
---

### Post by EvansFive on 2009-09-17
Just in case anyone is interested I got Ubuntu 9.04, Mac OS X 10.6.1 and rEFIt working together quite happily.

My iMac hdd has the following partitions:
1) EFI
2) Macintosh HD
3) linux swap
4) /boot (for Ubuntu)

All I changed was to remove the linux swap partition and create a new one with 128Mb preceding the new linux swap partition (using GPARTED).

The upgrade to 10.6.1 went ahead fine and I did not need to do anything with rEFIt...it all just worked.

So despite all the horror stories re 10.6.1 around on forums, it behaved very well for me this morning.

btw...I did make sure I had upgraded all software prior to the upgrade and did select Rosetta for install when installing 10.6.

---

