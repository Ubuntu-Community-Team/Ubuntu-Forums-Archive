---
title: "Couple of questions, Ubuntu specific and not."
date: 2006-07-18
forum: Apple PPC Users
---

### Post by Taiden on 2006-07-18
I got two major questions:

1) I want to make three partitions (not including swap and all that stuff). One for Ubuntu, one for OS X, and one for cross platform media. What format will be able to be read by both operating systems with the most ease and speed?

2) I am thinking of buying a new harddrive for my 2 USB white G3 ibook. A friend of mine pointed out that getting a 7200 RPM drive might be pointless because the computer wont be able to read the harddrive at full speed. it will be 600MHz with 640 mb of ram (100MHz fsb).

Thanks guys, I used to know all this stuff but I recently got into cars and computers are a little ahead of me right now.

---

### Post by halitech on 2006-07-18
not sure if Macs are different but my mother has an AMD Duron 700 and with a 5400 drive, it runs slower then with a 7200, not alot but enough that it is measurable. every system will always have a bottleneck so unless the price difference is alot, might as well go with the 7200 drivess.

---

### Post by scxtt on 2006-07-18
1. seems that OS X can read a ["UNIX file system"](http://www.kenstone.net/fcp_homepage/partitioning_tiger.html), so it looks like ext2 or ext3 should be readable by a mac ... and i'd imagine it can read FAT32, as linux can ...

2. i'd stick w/ a 5400RPM disk for a laptop ...

---

### Post by 3rdalbum on 2006-07-19
> **scxtt said:**
> 1. seems that OS X can read a ["UNIX file system"](http://www.kenstone.net/fcp_homepage/partitioning_tiger.html), so it looks like ext2 or ext3 should be readable by a mac ... and i'd imagine it can read FAT32, as linux can ...

Ext2 and Ext3 are not writable "out-of-the-box" on Mac OS X; you still need to install an extension for that functionality. Linux and OS X can read and write Fat32. They can also both read and write classic HFS (not HFS+).

---

