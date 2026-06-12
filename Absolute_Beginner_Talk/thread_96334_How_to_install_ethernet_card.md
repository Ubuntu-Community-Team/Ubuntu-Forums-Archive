---
title: "How to install ethernet card"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by ViGiLnT on 2005-11-28
I'm sorry for this noob question, but i cant figure this out...

When I was trying to get internet working on linux with my speed touch usb modem, i guess i uninstaled my ethernet support by mistake...

As you can see i have net here... but my ethernet card is no where to be found...

When I go to System>Administration>Network i can only see there my modem identified...

Help?

---

### Post by ssam on 2005-11-28
have a work through this [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643) it is some instructions for network trouble shooting

if you have problems at any stage let us know.

---

### Post by ViGiLnT on 2005-12-22
I haven't been able to go through that troubleshooting process due too lots and lots of work at my university, but I tried now to get it working.

In the first step of the tutorial (mii-tool eth0), the response i got was this:

SIOCGMIIPHY on 'eth0' failed: No such device

But when i did "lspci | grep Eth" i got this:

0000:00:03.0 Ethernet Controller: 3Com Corporation 3c556B CardBus [Tornado] (rev 20)

What should I do ?

---

