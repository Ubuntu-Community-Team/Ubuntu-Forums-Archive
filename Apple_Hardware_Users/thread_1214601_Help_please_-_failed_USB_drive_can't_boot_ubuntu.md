---
title: "Help please - failed USB drive can't boot ubuntu"
date: 2009-07-16
forum: Apple Hardware Users
---

### Post by EvansFive on 2009-07-16
I have a Powerpc iMac G5 which I have set up for dual boot (Mac OS X and Ubuntu 9.04).

There were two USB drives attached to the iMac.

The first one at /dev/sddb was in HFS+ format and had two partitions used for Mac OS X.

The second one at /dev/sddc was in Ubuntu format with three partitions ('/', '/home','/usr').  This is where all my Ubuntu stuff lives.

The drive in /dev/sddb has failed...and when I tried to boot Ubuntu it said it could not find /dev/sddc1...the boot process gave up and dropped into console mode.  It is trying to boot from /dev/sddc1 but it could not be found.  I guess because the failed drive had died and was not available my Ubuntu drive suddenly became /dev/sddb?????

The only way I could work around the problem was plug in a portable USB drive into the slot (/dev/sddb) where the previous failed drive was.  Thus allowing my Ubuntu drive to be /dev/sddc again!

The system started up but I cannot leave the portable USB drive plugged in all the time, it is needed elsewhere.

So can I do the following:
1) Remove the portable USB drive from the system (/dev/sddb)?
2) Somehow change Ubuntu to boot from my Ubuntu drive /dev/sdb1?
3) Reboot and all is well with me running my Ubuntu drive from /dev/sdb1?

If I can theoretically do the above how do I go about this please?  I am not an expert with Ubuntu or Linux so some detailed instructions would be very helpful please!

---

