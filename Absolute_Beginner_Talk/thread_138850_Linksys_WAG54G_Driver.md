---
title: "Linksys WAG54G Driver"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by Wibbles on 2006-03-02
Hey all,
Ive just install ubuntu and really like it, but Ive searched everywhere for a linux compatable driver for my router(in title). 
Could anyone show me where i can find one and how to install the driver itself? any help would be great.

thanks,

Wibbles :) \\:D/

---

### Post by Pragmatist on 2006-03-03
[http://www1.linksys.com/support/gpl.asp](http://www1.linksys.com/support/gpl.asp)

download it and type: ```
tar xvzf WAG54GV2-EU_v1.00.19_GPL.tgz
``` the change into the new directory that was created (it will have similar name to the .tgz file).  There you should find a README and hopefully also an INSTALL file.  Read these and come back if you need more help.

---

### Post by Q4U on 2006-03-03
I have the same router, but... it does not need a driver for Linux, it works out of the box. 

So, either 
1. you are looking for a driver for your wireless card (not for your wireless router), in which case you need to find the model of your card, or 
2. you want the firmware in your router (the previous poster included a link to the GPL source of this, useful if you want to take a look at how things work internally or if you want to hack it, but if you want to install a new version in  your router it is more handy to find the precompiled binary somewhere else in the Linksys website). Don't do it unless your router has a problem, or the firmware is obsolete, and in any case read the instruction in the router manual, as there is the risk to brick your router.

Q4U

Q4U

---

