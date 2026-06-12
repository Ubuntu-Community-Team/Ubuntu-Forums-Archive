---
title: "Desktop power management"
date: 2005-05-29
forum: Apple PPC Users
---

### Post by SpazTheCat on 2005-05-29
Hi,

I've installed Ubuntu 5.04 on my 15" LCD iMac and was fiddling with some basic power management but can't get things to work properly. The two problems I'm having are:

1. Display won't turn off. The screen just turns this kind of funky red/pink color. Is DPMS broken? I can see that it is turned on in the Xorg log.

2. I can't get the hard drive to spin down. I've edited hdparm.conf appropriately but still no deal. 

Thanks,
Andy

---

### Post by keifer on 2005-06-17
DPMS is broken, and while I have figured out how to spin down the harddrive, and turn of the monitor, DPMS needs to be fixed before this becomes usefull. Currently, you can put the computer to sleep, but when you wake it up, the DPMS screen locks up the system.

DPMS also causes problems when switching to a virtual terminal, and when you kill xorg.

---

