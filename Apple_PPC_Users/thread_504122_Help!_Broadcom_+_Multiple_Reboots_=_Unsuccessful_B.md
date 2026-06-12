---
title: "Help! Broadcom + Multiple Reboots = Unsuccessful Booting"
date: 2007-07-18
forum: Apple PPC Users
---

### Post by revision29 on 2007-07-18
I have successfully installed Fiesty Fawn (Kubuntu) flavor) on my 12" PowerBook (PPC).  Dual booting works great.  I set-up the gui just like I want to.  After booting into Kubuntu several times, I end up getting an error with the my broadcom card a.k.a. Airport Extreme.  This is no big deal, as I have figured out how to get it working after reading several tutorials.  The problem is that the x server never loads.  It just displays the error message every minute.  I removed the problem card, the error message no longer displays, but X does not load.  I don't even get a login prompt, as if there is a running process that has hung.  From what I have seen with others who have the same broadcom error message, their x server loads, but in the background the error message is displayed in the command line every minute.

I have not done anything significant to my settings and have not changes my hardware settings since installing.  In fact, I had this problem already, re-installed ubuntu and then the bandit strikes again.  Any ideas?

---

### Post by dougfractal on 2007-07-18
look at:
[http://blog.effraie.org/index.php/post/2006/10/20/Wifi-sous-ubuntu-ppc-avec-la-carte-Airport-extrem](http://blog.effraie.org/index.php/post/2006/10/20/Wifi-sous-ubuntu-ppc-avec-la-carte-Airport-extrem)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/76685](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/76685)
[http://ubuntuforums.org/showthread.php?t=142727&page=9](http://ubuntuforums.org/showthread.php?t=142727&page=9)

you may have to install edgy not fiesty.

airport2 firmware  [http://vrac.effraie.org/AppleAirPort2](http://vrac.effraie.org/AppleAirPort2)

---

### Post by ajmctaggart on 2007-07-19
Can you blacklist the Broadcomm Hardware and successfully boot?

---

