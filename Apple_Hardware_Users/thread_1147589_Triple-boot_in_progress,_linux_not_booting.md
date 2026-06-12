---
title: "Triple-boot in progress, linux not booting"
date: 2009-05-03
forum: Apple Hardware Users
---

### Post by cpufreak2589 on 2009-05-03
I am working on a fresh triple boot of osx/ubuntu 9.04/winxp on a macbook 5,1, following the guide here [http://ubuntuforums.org/showthread.php?p=7173021](http://ubuntuforums.org/showthread.php?p=7173021)

I have installed OSX, refit, and then installed ubuntu, creating a new partition for xp while I was installing. refit sees the ubuntu install at partition 3 (correct), but when I select linux, refit just hangs at the penguin. I'm not sure how to debug this and figure out what is going on, any suggestions?

EDIT 1: In OSX I ran First Aid on my linux partition and got error: "invalid sector size 0".

Edit 2: I booted into the 9.04 livecd and flagged the linux partition as bootable, as well as reinstalling grub using the guide here [http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11) but it still does not progress past tux on the boot menu

---

### Post by cyberdork33 on 2009-05-03
shutdown your computer and turn it back on a couple of times (not reboot).

---

