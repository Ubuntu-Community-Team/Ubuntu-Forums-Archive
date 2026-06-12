---
title: "USB wireless adapter (Ralink RT3070 chipset): my experience"
date: 2012-04-08
forum: Apple Hardware Users
---

### Post by heliboy on 2012-04-08
In case it helps the next guy/gal:  



                 The PL-H5DN-3070 USB wireless adapter works on an Intel PC, Ubuntu 10.04, kernel  2.6.32-38, if the rt2800usb module is blacklisted in  /etc/modprobe.d/blacklist.conf (which prevents loading of both the  rt2870sta module [which works], and the rt2800usb module [which does not  work]).  

The adapter does not work easily on a PPC Mac G4, Ubuntu 10.04, kernel  2.6.32-38, with  either of these modules. I tried many sources of the rt2870sta and its  cousins, including the CD that came with the unit and the manufacturer's  website, all of which failed, apparently because they include a  firmware loader that won't run on a PPC.  The rt2800usb  currently available through Ubuntu apparently is not up to the job, but  the latest version is said to be.  So I got the source for kernel 3.2.7  from kernel.org, compiled it (that was a bit of travail), and the adapter works  under the rt2800usb module.  In fact, it works very well.


I'm no pro at this stuff, so some of the above might be utter rubbish.

---

### Post by Paddy Landau on 2012-04-09
Thank you for posting this.

Please [mark your thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so that others with the same problem can more easily find it.

---

