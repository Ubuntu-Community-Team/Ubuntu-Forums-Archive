---
title: "installation woes"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2007-11-20
I just installed kubuntu in my laptop i had this issue with the modem.
now i my eagerness to install a driver for my modem i found this package thats
supposed to install winmodem drivers.  Apparently it doesnt worked.

So now I gave up on the idea that my modem could be used in Kubuntu, so now I 
proceeded in installing applications via wifi, everything seems to be ok except that when
I tried to install yakuake this is what I get:

```

Removing ltmodem-2.6.8-2-386 ...
[: 12: 0: unexpected operator
find: warning: you have specified the -mindepth option after a non-option argument -name, but options are not positional (-mindepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.


ERROR: Module lt_serial does not exist in /proc/modules
ERROR: Module ltserial does not exist in /proc/modules
ERROR: Module ltmodem does not exist in /proc/modules
ERROR: Module lt_modem does not exist in /proc/modules
Could not identify your distribution's way of automatically loading modules,
Exiting.

dpkg: error processing ltmodem-2.6.8-2-386 (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 ltmodem-2.6.8-2-386

```

I tried to do sudo apt-get install -f but it doesnt worked.
Any ideas?  

Thanks

---

