---
title: "eSATA Express Card on mid-2009 Macbook Pro - Working in Ubuntu, not on bootable USB"
date: 2015-09-26
forum: Apple Hardware Users
---

### Post by ac2334 on 2015-09-26
Hello,

Looking for a general solution to a particular issue that I am having..

On my mid-2009 Macbook Pro I have a Dynex 2-port eSATA express card and it works perfectly (and natively) under Ubuntu 15.04 using kernel 3.19.

For the purposes of data recovery, I need to work from a bootable-from-USB program found here:

[http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage)

No matter what I have tried, I can not get my external drive recognized. When I boot from the default kernel in GRUB the card is showing activity lights and the card IS recognized by the system, but the drive is not listed as a device..

Any advice appreciated..

Thank you!

---

### Post by howefield on 2015-09-26
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by ajgreeny on 2015-09-26
I know very little about Ubuntu on mac hardware but I do know that to mount and use a hard disk from a mac machine you will need to make sure that the system you are using has hfsplus and maybe also hfsutils and hfsprogs installed in order to mount the disks.

Make sure they are installed on the live SystemRescueCD, (though how you do that on it I am not sure, as I've never used it), and see if that helps.

Can you also clarify what you mean by "the card IS recognized by the system, but the drive is not listed as a device."  That seems like a bit of a contradiction.

---

