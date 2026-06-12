---
title: "reinstall sound drivers"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by benevolent on 2007-11-04
hello


how can i reinstall the sound drivers???


I have soundblaster audigy ES and i have no sound....only ffsssssssss :/ :(:(


thx....

---

### Post by kyphi on 2007-11-04
The Audigy ES uses the same driver as the Soundblaster Live.  See

[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs)

The driver is already in the kernel.

Have you enabled sound in Sound preferences? (System -> Preferences -> Sound)

Is the volume control in the top right corner of your desktop adjusted?

---

### Post by benevolent on 2007-11-04
I've tried to do that @post#8 -> [http://ubuntuforums.org/showthread.php?t=545784&highlight=sound+suse](http://ubuntuforums.org/showthread.php?t=545784&highlight=sound+suse)

> [ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver)
i downloaded the package
alsa-driver-hg20070526.tar.bz2 dated 05/26/2007
renamed it to alsa-driver.tar.bz2 for ease of installation.
then executed the following commands in the terminal
$tar xvf alsa-driver.tar.bz2
$./configure
$sudo make
$sudo make install



and now i have this :/

> dimitris@ubuntu:~$ aplay -l
aplay: device_list:204: no soundcards found...

---

### Post by benevolent on 2007-11-04
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)


I follow some steps of this VERY helpful thread, and maybe i'vegot it....

sudo shutdown -r now :)



edit: SOLVED

---

