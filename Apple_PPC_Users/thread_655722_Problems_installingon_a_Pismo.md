---
title: "Problems installingon a Pismo"
date: 2008-01-01
forum: Apple PPC Users
---

### Post by gobabushka on 2008-01-01
first of all, my cd drive is a slave, so I changed the cd alias in OF to /pci@f2000000/mac-io@17/media-bay@34/ata-3@20000/disk@1

Then I boot the cd by typing in boot cd:,\install\yaboot

then at the yaboot prompt i used the foloowing command:

"live-nosplash-powerpc video=ofonly break=top"

For some reason it keeps dumping me into busybox saying that the target filesystem doesn't have /sbin/init
I've tried modprobing ide-core to no avail. Any suggestions?

---

### Post by cryptocoryne on 2008-01-03
I couldn't install ubuntu or any other PPC distribution on a G3 powerbook lombard.
I had the same sort of problems you're having. After too much hassle, I was able to install Debian Etch. (I can't figure out why Debian would install and all the others wouldn't. I didn't do anything differently. modprobing ide-core didn't do anything.) Things were good for like three days. Then the logs started showing all sorts of disk errors and the filesystem got corrupted. 

I thought maybe my hard drive was failing, so I tried another. The filesystem got corrupted again.  I tried turning off DMA and no apic but the same flakey hard disk problems just kept coming back.  I gave up and just installed Panther, which seems to run fine. I think there's something wrong with the PPC IDE modules, but this problem is too low level for a casual linux hobbyist like me to figure out.

---

### Post by chayzer on 2008-01-03
Which version of live cd are you using?

---

### Post by gobabushka on 2008-01-05
im using the latest stable release

---

### Post by chayzer on 2008-01-06
I had the same problems with the newest disk too. Try finding a 7.04 version..

---

