---
title: "[SOLVED] supergrub download site?"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by bhold on 2007-10-12
I'm having trouble making a supergrub cd. Can anyone recommend a good download site, preferably one that provides md5sum information for the iso file?     Thanks   -- Bob

---

### Post by Pumalite on 2007-10-12
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by bhold on 2007-10-12
Tried that site. Downloaded cd version 9598, unzipped, right-click on the ISO file, select "write to disk". Writes for a few minutes, says "finishhing write", hums a few more seconds.... "error writing to disk". 3 times in a row now. I have tried burning at high, medium, and low speeds.

I had no problem creating a bootable gparted cd a few days ago so have no reason to think I have a bad batch of cd-r's or that my steps are wrong. md5sum value for the iso file would be handy, but I did not find it posted anywhere at the download site.

As far as I know my dvd / cd drive is working fine. I created and tested backups earlier today, they were fine..

I downloaded the supergrub iso each time before burning so am not sure how to proceed from here. I would really like to get supergrub and play around with it before I set up dual boot for Gutsy / Suse 10.3 in a week or two.

---

### Post by Duck2006 on 2007-10-12
You can download a ISO from this site

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Pumalite on 2007-10-12
Or this:

[http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html](http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html)

---

### Post by bhold on 2007-10-13
Thanks for suggestions for this problem. I finally got a working supergrub disk today, from download of sgd_0.9642.iso.

Probably some or all of the disks I burned yesterday were OK. Here were my problems:

1. To burn, I right-click on the downloaded iso file and select "write to disk". This burns the cd with the default burner, not sure what it is called. Beware, this software seems to give false error messages upon completion of burning a cd-r. I never get this message upon completion of burning to dvd+rw.

2. Being suspicious that the cd might really be ok even though I got an error message on the burn, I tried to boot from it. Hitting F12, getting into the boot menu, and selecting "Boot from CD" did not work - hung keyboard IO and I needed to power cycle. Instead, I tried changing the boot device sequence moving CD above Hard disk. Now I was able to boot from the supergrub CD.

My 2 cents worth during this exercise - maybe it will save someone else some time and some extra CDs.

---

### Post by Pumalite on 2007-10-13
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by ippokratis on 2007-11-30
Let's say we download an ISO file.  How we use this "md5sum" to check the CD?

---

