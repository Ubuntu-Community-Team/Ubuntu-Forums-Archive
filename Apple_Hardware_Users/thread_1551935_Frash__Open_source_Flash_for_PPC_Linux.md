---
title: "Frash:  Open source Flash for PPC Linux?"
date: 2010-08-12
forum: Apple Hardware Users
---

### Post by New Horizon on 2010-08-12
I saw that the sources for flash 10 were ported to iphone and ipad recently and were also used on some other platforms.

Is there any chance this could be used to build a working copy of flash for PPC Ubuntu?

Sources are here:

[http://github.com/comex/frash](http://github.com/comex/frash)

---

### Post by linuxopjemac on 2010-08-13
Lightspark will bring Flash support to PPC in 0.4.3.
[http://mac.linux.be/content/lightspark-will-bring-flash-support-linux-ppc-users](http://mac.linux.be/content/lightspark-will-bring-flash-support-linux-ppc-users)

---

### Post by New Horizon on 2010-08-21
How compatible would this be compared to Frash though I wonder?  From what I've read, Frash is essentially a real PPC build of the Adobe Flash code.  If Frash could be built for PPC, wouldn't it be better than lightspark?

---

### Post by paul_mcl on 2010-08-22
Built Lightspark 0.4.3 for Linux PPC. You'll also need the following file (place it into ./platforms/): [http://github.com/kronat/lightspark/raw/b6b68d267c67cdb0ab7a8cdec9d070df4bb3cdce/fastpaths_ppc.cpp](http://github.com/kronat/lightspark/raw/b6b68d267c67cdb0ab7a8cdec9d070df4bb3cdce/fastpaths_ppc.cpp) to build lightspark successfully.

---

### Post by New Horizon on 2010-08-22
> **paul_mcl said:**
> Built Lightspark 0.4.3 for Linux PPC. You'll also need the following file (place it into ./platforms/): [http://github.com/kronat/lightspark/raw/b6b68d267c67cdb0ab7a8cdec9d070df4bb3cdce/fastpaths_ppc.cpp](http://github.com/kronat/lightspark/raw/b6b68d267c67cdb0ab7a8cdec9d070df4bb3cdce/fastpaths_ppc.cpp) to build lightspark successfully.

Does it work well?  Are you able to watch everything?

---

### Post by MacPenguin1972 on 2010-08-23
> **linuxopjemac said:**
> Lightspark will bring Flash support to PPC in 0.4.3.
[http://mac.linux.be/content/lightspark-will-bring-flash-support-linux-ppc-users](http://mac.linux.be/content/lightspark-will-bring-flash-support-linux-ppc-users)


Hello,

Wanted to know- do you know when they will release this new Lightspark program? And also, will you be able to play Flash games? Like on Facebook for example? 

Thanks,
MacPenguin

---

