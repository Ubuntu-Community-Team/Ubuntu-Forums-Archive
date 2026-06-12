---
title: "Make persistent USB stick from Live USB on MacBook?"
date: 2016-06-22
forum: Apple Hardware Users
---

### Post by bradpatrick2 on 2016-06-22
Hello:

I successfully created a Live USB stick for 16.04 and would like to now create a persistent 16.04 Live USB on a SanDisk 32GB stick. It would be nice to keep the correct screen preferences, wifi passwords, etc. instead of losing them all with each reboot, plus a little storage.  Can I install from the main boot screen (or desktop installer) to the new 32GB USB stick directly? This seems like something that really ought to be simple to do. Many of the pages I have looked at already are years old and one indicated persistent was removed from the 16.04 installer for some reason.

So, what is the easiest way to create a persistent Live USB install of 16.04 on a MacBook Pro (2015) where I have an existing Live USB boot stick which works fine?

Many thanks!

BP

---

### Post by howefield on 2016-06-22
Welcome to the forums, thread moved to the "*Apple Hardware Users*" forum.

---

### Post by C.S.Cameron on 2016-06-22
I've had problems making persistent partitions in 16.04, mkusb worked for me on non-apple machine.
If mkusb does not work on an apple, you should be able to obtain a blank casper-rw file, stick it in the root of the drive and edit the syslinux.cfg or txt.cfg or text.cfg by adding <space>persistent after the "--"

---

