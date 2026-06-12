---
title: "connecting to the internet"
date: 2005-10-06
forum: Apple PPC Users
---

### Post by calcioguy9 on 2005-10-06
I'm running a livecd on my ibook and it's booting up great, and everything seems to be working well, except I can't connect to the internet.  In my apartment we have a Linksys WRT54g wireless router that works perfectly when I'm using OS X.  I also tried using an ethernet cable to hook up to the net but that didn' work either.  If you can't tell I'm new to linux and ubuntu, but I'm trying to learn.  Thanks for any help.

---

### Post by foulmouth on 2005-10-06
A reason why your wireless connection isn't working might be because of airport extreme wireless card. This is unfortunately a problem that can't be remedied due to a lack of linux driver support by broadcom, the creators of the airport extreme. There are projects out there that are working on reverse engineering the broadcom chipset that is used in the airport extreme:
quote from the gentoo forums:
"
For more details on the native AE driver's progress, please see: [http://bcm43xx.berlios.de](http://bcm43xx.berlios.de)
The reverse engineering project is located at: [http://linux-bcom4301.sf.net](http://linux-bcom4301.sf.net) and our spec sheets are located at [http://bcm-specs.sipsolutions.net](http://bcm-specs.sipsolutions.net)
"
Here is a topic that might be of interest to anyone willing to use Mac On Linux to get their ae working
[http://forums.gentoo.org/viewtopic-t-365647-start-0.html](http://forums.gentoo.org/viewtopic-t-365647-start-0.html)

As for your ethernet connection there could be any number of reasons for that. Do you have any more info?

---

