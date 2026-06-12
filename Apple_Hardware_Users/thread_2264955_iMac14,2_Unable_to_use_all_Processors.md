---
title: "iMac14,2 Unable to use all Processors"
date: 2015-02-11
forum: Apple Hardware Users
---

### Post by Mike_Tonks on 2015-02-11
Ubuntu version: 14.10 (upgraded from 14.04)

Unable to boot without nolapic option, which leaves me with only 1 cpu.  Machine is horribly slow, for serious tasks this is no good.

lshw says CPU is: Intel(R) Core(TM) i5-4570 CPU @ 3.20GHz

The strange thing is, it has worked with all 4 cores, and worked really well.  After upgrading to 14.10 it was all fine, all cores working, booting up fine.  Then 1 day it wouldn't boot, and I have to resort to nolapic.  Another time it did boot up fine with all cores, but now for at least a month it never will.

I install regular updates etc.

Can anyone help me to get those processors working?

-- update --

I resinstalled 14.04 to attempt to fix the issue, which did not work.  But I noticed that when running from the live USB , all cores were active.  Further investigation led me to try booting from USB using a supergrub2 image, which allowed me to select my hard disk installation and boot from that.  This worked, and systems runs with all cores (but only as I say booting from the USB key, not from the hard disk).

... The plot thickens ...

So probably it's a grub issue?  I will try putting the supergrub on hard disk, but meanwhile hopefully someone might know more about this area and be able to advise.

---

