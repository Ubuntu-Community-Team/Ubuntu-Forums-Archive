---
title: "Problems with the sound"
date: 2010-06-01
forum: Apple Hardware Users
---

### Post by nikitchm on 2010-06-01
Hey everybody,  I've got a problem with sound - it's complete absence. Tried installing version 1.0.23, as explained here, [http://swiss.ubuntuforums.org/showthread.php?t=1292587](http://swiss.ubuntuforums.org/showthread.php?t=1292587), and here, [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/comment-page-1/#comment-669](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/comment-page-1/#comment-669), and except for the output of "cat /proc/asound/version" which claims I still have 1.0.22.1 version installed it went fine. Actually, alsaconfig, at the same time, is of 1.0.23 version and executed with an exclamation that everything should work now. "dmesg | grep "snd_" returns zero result. Everything is unmuted (with alsamixer). I did stop alsa before doing all the installations (with "alsa-utils stop"). No mistakes were reported during the installation. I tried doing it twice, restarting each time following installation.  I have Mac Intel Xeon computer with Ubuntu 10.04 with all the current upgrades installed in dual boot with original Mac OS X 10.6.3.  Would appreciate any help or advice.  Thank you

---

