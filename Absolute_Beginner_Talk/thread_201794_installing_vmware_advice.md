---
title: "installing vmware advice"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by sbguy on 2006-06-22
I just had a three-day nightmare installing vmware-reader and I want to add one piece of advice that I couldn't find here. Basically if you do a fresh install of Dapper I advise you not to "update everything but the kernel" before installing vmware-player. (I read somewhere it won't work with the new kernel, which is wrong) I did this, ran sudo apt-get install vmware-player and got a message about a dependency on vmware-player-kernel-modules. Added that package in the command and got a message about a dependency on vmware-player-kernel-modules-2.6.15.25 which was strange given I was on 2.6.15.23. Did a full update, made sure I had the latest versions of the vmware-player-kernel source and module packages, and everything else, ran the command again and it installed with no problems. Maybe I updated something I shouldn't have before doing the install, anyway hope it helps.

---

### Post by bluenova on 2006-06-22
Perhaps you had to have vmware-player, but I find the easiest is vmware-server using this guide:
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

---

### Post by az on 2006-06-22
It sounds like you installed packages by hand (downloaded and then ran dpkg -i *package*)

Had you added the multiverse repo to your list and then used the package manager, you would have been fine.  It would have taken care of all the dependencies for you.

There is no need to compile it from source.

---

