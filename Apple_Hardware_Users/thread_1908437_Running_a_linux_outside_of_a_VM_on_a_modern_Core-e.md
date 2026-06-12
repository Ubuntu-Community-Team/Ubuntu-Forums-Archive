---
title: "Running a linux outside of a VM on a modern Core-equipped Mac can quickly lead to..."
date: 2012-01-13
forum: Apple Hardware Users
---

### Post by felixdzerzhinsky on 2012-01-13
How accurate is this statement I got on #apple on freenode irc?:

>  Two points to know. 1) Apple's EFI implementation only understands GPT and protected-GPT. With the Compatibility Module installed, protected-GPT partitions appear as MBR. Common bootloaders do not understand protected-GPT, and they will damage the partition table so that the Mac cannot boot *anything*. 2) Running a linux outside of a VM on a modern Core-equipped Mac can quickly lead to catastrophic CPU failure.

---

### Post by 2F4U on 2012-01-13
******** from Mac fanboys. I am running Ubuntu exclusively on a MacBook without any problems. Also see here:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

If it would be true what they say then anybody else who is running Linux on a Mac must be wrong.

---

### Post by felixdzerzhinsky on 2012-01-13
> **2F4U said:**
> ******** from Mac fanboys. I am running Ubuntu exclusively on a MacBook without any problems. Also see here:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

If it would be true what they say then anybody else who is running Linux on a Mac must be wrong.

Is your a late model mac from 2011?  My 2006 Intel iMac ran well. I was taken aback when rEFIt did not work with the new one Lion though.

[http://scottlinux.com/2011/06/14/how-to-dual-boot-os-x-and-linux/](http://scottlinux.com/2011/06/14/how-to-dual-boot-os-x-and-linux/)

And I now discover Apple were too cheap to put a recovery DVD or USB in the box.

---

### Post by localhost8080 on 2012-01-15
apple have put a recovery option in the firmware:
you can re-install lion over the internet without booting the harddrive

[http://www.apple.com/macosx/recovery/](http://www.apple.com/macosx/recovery/)

:D

---

### Post by Q-collective on 2012-01-15
> **localhost8080 said:**
> apple have put a recovery option in the firmware:
you can re-install lion over the internet without booting the harddrive

[http://www.apple.com/macosx/recovery/](http://www.apple.com/macosx/recovery/)

:D

This will *only* work on the late-2011 models (or later) by default or on the older models that are completely up to date in OS X Lion (so they installed the latest firmware versions that are required).

---

### Post by felixdzerzhinsky on 2012-01-24
> **2F4U said:**
> ******** from Mac fanboys. I am running Ubuntu exclusively on a MacBook without any problems. Also see here:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

If it would be true what they say then anybody else who is running Linux on a Mac must be wrong.

It sounded a bit over the top. Still looking for a clear document on how to dual boot OS X Lion on a 27 inch, Mid 2011 iMac.

I prefer to keep an OS X partition just in case there is a hardware issue so the repair guy knows what he is doing.

---

### Post by markbl on 2012-01-24
> **localhost8080 said:**
> apple have put a recovery option in the firmware:
you can re-install lion over the internet without booting the harddrive
Just to confirm this -  I accidently deleted the EFI partition on my new 2011 MBA a couple of months ago so I wanted to restore the HD completely as new. I booted with option-R, waited about 10 mins for it to load over the net, ran the disk utility, re-partitioned from scratch with the "1 partition" option, then Lion downloaded and installed itself over the net. Took a couple of hours but worked well.

---

