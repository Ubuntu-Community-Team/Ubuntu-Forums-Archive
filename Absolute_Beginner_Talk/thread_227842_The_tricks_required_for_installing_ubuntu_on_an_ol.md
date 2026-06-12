---
title: "The tricks required for installing ubuntu on an old Pentium 2 box"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by andersja on 2006-08-02
Hi all,

thanks to the ubuntu forums, I managet to get my future home server flying last night: installing on old hardware wasn't entirely click and play, however, therefore I thought I should share my experiences with the wider community:

[http://www.jacobsen.no/anders/blog/archives/2006/08/02/ubuntu_home_server_setup.html]("http://www.jacobsen.no/anders/blog/archives/2006/08/02/ubuntu_home_server_setup.html")

I bought some RAM upgrades and two 320 Gb disks, and then set about installing:

> Once the RAM and the harddrives were in place, the default CD didn't want to boot. I got some non-intuitive error messages that needed a bit of Googling to resolve:

    * Buffer I/O error on device ... meant one needed to tell ubuntu to [irqpoll]("http://www.ubuntuforums.org/showthread.php?t=220703")
    * RAMDISK ran out of compressed data, invalid compression format (err=1), kernal panic - not syncing: UFS Unable to mount root fs on uknown block - luckily [someone had gotten this one before me]("http://www.ubuntuforums.org/showthread.php?p=1313096")
    * Later, having started the installer, it suddenly changed its mind and didn't want to recognize the CD-ROM any more. Again, someone else had done some digging, and [ide=nodma solved it for me.]("http://techheadaches.blogspot.com/2006/06/ubuntu-606-wont-install-cd-rom-couldnt.html")

Summary: to get ubuntu flying on my old PII, I needed to use the 'alternate' CD, select 'install in text mode' and before installing, hit F6 and enter irqpoll ide=nodma

---

