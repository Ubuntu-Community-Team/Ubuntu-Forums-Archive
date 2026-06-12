---
title: "Dual Boot Ubuntu &amp; Mac OS on PowerMac G5"
date: 2010-05-04
forum: Apple Hardware Users
---

### Post by jackacase on 2010-05-04
I just received an old PowerMac G5, and I really want to put Ubuntu on it. I've found an installation of "Hardy Heron," that it can boot from as a live CD. Firstly, is it possible to setup dual boot Ubuntu and MacOS, and secondly, is that the latest version for PowerMac:confused: If anyone could describe the steps plainly, I would be very grateful.

---

### Post by linuxopjemac on 2010-05-04
Your version is certainly not the latest version. Dual boot is possible, it will be possible thanks to yaboot. I recommend you to read some stuff about this subject. I give you some links to start with:
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
[http://mac.linux.be/content/apple-powerpc-wiki](http://mac.linux.be/content/apple-powerpc-wiki)
[http://mac.linux.be/phpBB3/viewforum.php?f=9](http://mac.linux.be/phpBB3/viewforum.php?f=9)

and last but not least, the search bar in the top at the right hand side in this forum.

---

### Post by jackacase on 2010-05-04
Thanks a lot for the info, I hope I can get it to work.

---

### Post by jackacase on 2010-05-04
Two questions. How exactly do you edit yaboot once you bring it up in the terminal with
sudo nano /etc/yaboot.conf? Also, which command would default it to Ubuntu, but still allow you to boot into OSX

---

### Post by linuxopjemac on 2010-05-05
I think all of your answers can be solved when you read [this page]("http://mac.linux.be/content/yaboot").

---

### Post by jackacase on 2010-05-05
You know, I really shouldn't have worried, once i got Lucid for powerpc, all I needed to do was to use the preinstalled partition manager, free up some space and install. Thanks a lot for all of your help.

---

