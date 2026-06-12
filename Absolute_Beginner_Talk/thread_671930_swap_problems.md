---
title: "swap problems"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by mrxtambourineman on 2008-01-19
When I try to install uswsusp I get to the configure screen and it tells me:  

The swap file or partition that was found in uswsusp's configuration      &#9474;  
 &#9474; file is not active. In most cases this means userspace software suspend   &#9474;  
 &#9474; will not work for you and you will need to choose (or let uswsusp         &#9474;  
 &#9474; choose) another swap space. In some corner cases however, this can be     &#9474;  
 &#9474; what you want.                                                            &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Continue without a valid swap space?                                      &#9474;  
 &#9474;                                                                           &#9474;  

Does this mean my swap drive is turned off? How can I fix this?

Thank you for your time.

---

### Post by intel on 2008-01-19
how to acivate swap manually
#swapon /dev/hda2

(read man swapon for more info)

for more info about ATI Radeon X1200 series join the following support group
https://groups.google.com/group/x1250

---

### Post by amo-ej1 on 2008-01-19
open a console en type 'free -m'

this will show you the current memory usage and swapspace occupation. If the total for swap says '0' it means no swapspace is currently active.

Setting up swapspace the normal way involves having a partition (for swsuspend it should equal the size of your physical ram, since you physical ram gets written to it during suspend). The you should create a swapspace in it (mkswap /dev/myswapartition) and it should be added in /etc/fstab to be mounted on boot.

---

### Post by mrxtambourineman on 2008-01-19
I'm guessing my swap is on because the total is not 0. However, my swap has 0 used. I still can't figure out how to get uswsusp to work right--any suggestions?

---

