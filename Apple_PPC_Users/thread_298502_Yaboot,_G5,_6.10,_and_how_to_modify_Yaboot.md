---
title: "Yaboot, G5, 6.10, and how to modify Yaboot"
date: 2006-11-12
forum: Apple PPC Users
---

### Post by amishman on 2006-11-12
OK, I seem to be getting no where installing Ubuntu 6.10.  I can install and reboot to get to the Yaboot screen but typing L for Linux does not load Linux.  I have installed twice now and two different drives.  1st drive was a 120GB Western Digital drive.  When that did not work I thought to myself maybe this is a drive issue.  So, purchased a new 400GB SATA drive for my 2GHz G5 today and installed in slot A and slot B has the stock Apple 160GB drive.  I removed the 120GB WD drive all together.  Both drives have the same issue and I am betting the Yaboot file is just not correct and needs to somehow me opened and adjusted and then it would work.  I can't see paying $250 for Ubuntu's tech support as spending that much just does not make sense for tinkering with an open OS like Linux.  So, anyone on this board that has a clue on how to modify the Yaboot file and would this help.  Like I said, install goes fine.  Yaboot just does not load Linux.  My guess this is a Yaboot issue and not that Linux was not installed correct.  I installed twice on two drives so unless it just hates a G5 2GHz system, I am getting no where.  Kinda frustrating and I would think others have gone through this same issue and there must be a more knowledgeable Ubuntu rep online here that can offer guidance.  I see nothing in their tech files about this so...

Thanks

tj

---

### Post by organicchunkysalsa on 2006-11-30
I have the exact same problem on my g5 tower 1.8ghz single. If anyone can shed some light on this please do, this is rather ridiculous.

---

### Post by stream303 on 2006-11-30
With all that drive-swapping, I'm wondering if the PRAM is corrupted?

Perhaps holding down ctrl-option-p-r after putting your drives in the bays you are going to leave them in, and turning it on and waiting for the chime before releasing might help.  If that semi-works, I wonder if a reinstall with a clean pram might be in order..

Here's some more info:
[http://www.apple.com/support/mac101/help/2/](http://www.apple.com/support/mac101/help/2/)

---

### Post by linear on 2006-11-30
If you believe it's a problem with yaboot.conf, can you boot from a Live CD, locate /etc/yaboot.conf on the internal disk, and post it here so others can look at it? Someone may be able to spot the problem.

There is also some info [here]("http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/ch9.en.shtml") on loading yaboot manually from Open Firmware.

---

