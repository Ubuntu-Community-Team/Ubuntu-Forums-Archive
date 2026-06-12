---
title: "Ubuntu installation iMac g3 no hd detection"
date: 2010-01-17
forum: Apple Hardware Users
---

### Post by sunseeker21 on 2010-01-17
Hello!:)

I'm new here, and I'm new with Ubuntu too. But I really need some help!

A friend of mine just bought a iMac g3 (lime), without knowing any technical detail (we don't know year, type, nor ram, hdd, processor... nothing!) But another friend of mine told me to try to install Ubuntu (alternate version for ppc), that it would have been great with this machine. 
Unfortunately, as I run the cd-live installation, when the iMac tries to detect the hardware disk, it doesn't find it! 
It asks me to select a driver from a list (a very long one!) but I can't figure out which one is the right one, and what's wrong with the mac!
I have been searching through other threads here on this forum, without finding anything similar to my case! 

Can anyone help me please!!! It's almost a week that I'm trying to install Ubuntu on this iMac, and I'm a little bit short of ideas right now (and a little bit desperate too!!!!)

Thank you in advance!! ;) 
(if this thread is not in the right place, please let me know, I'll remove it immediately!)

---

### Post by B_Free on 2010-01-17
Is there a Mac OS on the machine?

---

### Post by linuxopjemac on 2010-01-18
Let me give you a simple answer, try Debian Lenny. It will work out of the box. The only thing that might not work is X. See [here ]("http://mac.linux.be/content/cross-distribution-issues")for a working Xorg.conf.

if you really want to try Ubuntu and you are a beginner, I advise you to follow a thread, like [here]("http://mac.linux.be/content/xubuntu-g3-ibook") or [here]("http://mac.linux.be/content/kubuntu-ibook-g3").

The bottom line is that a graphical installer in (*)Ubuntu won't work as the correct Xorg.conf is not made. You have to manually set it before. If you really would like to have (*)Ubuntu, I would go for a cli-installation. Boot the burned CD pressing C at bootup. At the first (yaboot) prompt, press TAB and then choose cli-powerpc. That should give you a basic system to start from. After installation you can install a desktop interface like XFCE or Gnome.

I also read a thread somewhere that the hard drive in the blue and white G3 is not recognised, see [here]("http://ubuntuforums.org/showthread.php?t=1374285"). The guy has a solution.

---

### Post by sunseeker21 on 2010-01-18
Thank you!!!!

The machine doesn't have Mac OS on, that was the only info we had about the iMac!!

I'll go and try Linuxopjemac's instructions!!! I'll try out Debian Lenny! Thanks a lot!! Really!!! I'll let you know!! ;)

Thank you!!:D

---

### Post by B_Free on 2010-01-18
A Lime iMac is either a 266 or 333 speed. The HD is a 6 gig or 8 gig. The CD drive is tray loading. 32 MB RAM was standard. The RAM needs to be 256 or more for any Ubuntu to work. If you could find a copy of a Mac OS 10.2 or older you could find out exactly what you have. 8.6 or 9 will also work

---

### Post by linuxopjemac on 2010-01-18
there is another thread [here]("http://ubuntuforums.org/showthread.php?t=1384359") with xubuntu on an iMac G3 /266. It should work for your type of computer too.

---

### Post by sunseeker21 on 2010-01-18
Thank you everyone! 

I've tried different installations until now, but nothing has changed, I still have the same problem, with different types of OS... so I really think there are no hard drives in the iMac... 

the guys from which we bought it told us that only the Mac OS was uninstalled, but said nothing about the hard drives... even if it sounds a little strange to me though...

Btw, thanks a lot for your help!! 

Grazie! ;)

---

### Post by linuxopjemac on 2010-01-19
if you can start MacOS without a CD, there is a hard drive ;)

---

