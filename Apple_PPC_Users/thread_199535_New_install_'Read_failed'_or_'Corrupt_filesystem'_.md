---
title: "New install: 'Read failed' or 'Corrupt filesystem' errors on Lombard Powerbook"
date: 2006-06-18
forum: Apple PPC Users
---

### Post by misterdham on 2006-06-18
Hi,

I am trying to install Ubuntu 6.06 on a G3 400 Lombard. I burned one install CD from the ISO I downloaded, and the furthest I got was the first time I tried to install. After hitting 'Enter' on the Open Firmware screen, it displayed an Ubuntu logo and was running something when it stopped. I don't recall what it did then.

On many subsequent retries, it would do one of the following:

* It would start to load the RAM disk, and then these messages would appear:

PCI: Cannot allocate resource region 1 of device [...blah...]
RAMDISK: Ran out of compressed data
invalid compressed format (err=1)
Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(1,0)

* Many times it would simply say "read failed."

* A couple of times it said "[directory path]/unknown or corrupt filesystem."

I tried this on two burned CDs, one done at 16x and one done at 4x. Both verified as OK after the burn.

I also tried erasing and reformatting the hard drive before install, no dice.

Is there any hope for me? is my laptop totally FUBAR?

Thanks for any advice you can offer,

OK
DAH

---

### Post by misterdham on 2006-06-18
I repartitioned the HD and tried again. This time it got to the screen with the Ubuntu logo on it, but it stopped at "Creating Live CD User..." and then went to a DOS-looking screen with this error:

PCI: Cannot allocate resource region 1 of device 0000:00:11.0

And then it hung up.

---

