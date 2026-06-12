---
title: "installing a screencaster."
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by tonzofgunz25 on 2007-07-19
I was trying to download and install recordmydesktop...
and this is the error i get. (i've gotten the same thing for alot of things that i've tried to install)
ERROR: FAILED TO SATISFY ALL DEPENDENCIES (broken cache)

:confused:

anyone else figure out how to get around it?

---

### Post by jfinkels on 2007-07-21
> **tonzofgunz25 said:**
> I was trying to download and install recordmydesktop...
and this is the error i get. (i've gotten the same thing for alot of things that i've tried to install)
ERROR: FAILED TO SATISFY ALL DEPENDENCIES (broken cache)

:confused:

anyone else figure out how to get around it?

For general information on installing programs in Ubuntu, click the link in my signature called "Installing Software". 

If you have Ubuntu 7.04 Feisty Fawn, recordmydesktop (and the graphical version, gtk-recordmydesktop) are in the software repositories (as shown here [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=recordmydesktop&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=recordmydesktop&searchon=names&subword=1&version=feisty&release=all)). You can install it by typing in the terminal ("Applications > Accessories > Terminal"):```
sudo aptitude install recordmydesktop
```

If you have an earlier version, follow the directions in this thread: [http://ubuntuforums.org/showthread.php?t=294605](http://ubuntuforums.org/showthread.php?t=294605)

If you are still having problems installing, please post clearly and concisely what actions you took and the full error message you are getting.

---

