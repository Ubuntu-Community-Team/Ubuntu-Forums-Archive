---
title: "usb drive not working"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by pheryllt on 2008-01-09
upgraded to the new 7.10 and not when I plug in my cell phone to use the sim card to transfer files it wont mount it.  It worked flawlessly in fiesty but everytime I plug it in now it sees it as a Motorola V3 series Music Player but will not mount it.  Have run dmesg | tail and this is the response: 

[171137.864000] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[171137.864000] sd 7:0:0:0: [sdb] Sense Key : Medium Error [current] 
[171137.864000] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[171137.864000] end_request: I/O error, dev sdb, sector 237
[171137.864000] printk: 151 messages suppressed.
[171137.864000] Buffer I/O error on device sdb1, logical block 0
[171138.008000] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[171138.008000] sd 7:0:0:0: [sdb] Sense Key : Medium Error [current] 
[171138.008000] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[171138.008000] end_request: I/O error, dev sdb, sector 238



Any ideas or hints as to what the problem is as I never had a problem while in fiesty only since I did fresh install to gutsy and really dont want to downgrade as gutsy works awesome otherwise

---

### Post by moffa on 2008-01-13
Try 'fdisk -l' and then mount that to /media/disk or some path that exists

---

### Post by warrior24 on 2008-01-13
I use moto4lin to transfer files form my Razor.

---

