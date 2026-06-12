---
title: "ubuntu can not be started"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by soulwind on 2007-10-28
I was trying to install ati driver as it show in [http://ubuntuforums.org/showthread.php?t=575843&highlight=ati+radeon+9600xt](http://ubuntuforums.org/showthread.php?t=575843&highlight=ati+radeon+9600xt)

I rebooted my computer at step 8 and I can only log on at "failsafe Gnome" session. when I try to log on on normal session it just sends me back to log on screen. is there anything I can do o recover my system??

---

### Post by Cato2 on 2007-10-28
I guess you are using Ubuntu 7.10 (Gutsy).  If so, you can probably recover things using Gutsy's new 'Bulletproof X' feature: [http://arstechnica.com/journals/linux.ars/2007/08/29/ubuntu-xorg-maintainer-demonstrates-bulletproof-x](http://arstechnica.com/journals/linux.ars/2007/08/29/ubuntu-xorg-maintainer-demonstrates-bulletproof-x)

See my comment on how to use this at [http://ubuntuforums.org/showthread.php?p=3642888&mode=threaded#post3642888](http://ubuntuforums.org/showthread.php?p=3642888&mode=threaded#post3642888) - it was for someone using an Nvidia driver, but the recovery process is generic and should work for any video driver problems.

Also, have you tried simply running the Ubuntu Restricted Drivers Manager - this is a really easy way to install binary drivers in Ubuntu 7.04 or later. See [http://www.michaellarabel.com/?k=blog&i=114](http://www.michaellarabel.com/?k=blog&i=114) for some nice screenshots.

The best guide I've seen to installing restricted (binary) drivers for Ubuntu is at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) - this uses Restricted Drivers Manager and see the section on Ubuntu 7.04 and 7.10.

---

