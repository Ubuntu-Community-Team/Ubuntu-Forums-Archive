---
title: "Crystal CS423x device no sound"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by TLM on 2007-03-13
I had Debian installed on the box(old Dell Optiplex  GX1 with pentiumIII 450 got cheap from outsourcer closing office. 512MB ram 6 GB hd (I know)), decided to switch to Ubuntu, got it installed after having an issue with the CD drive. no sound so I followed all the different threads I could find then I found:

[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449) 

and followed that one. Picked closest drivers from the list but it still errored out. I see the card in the device manager with the sb/wss/opl3emulation, mpu401 and the control.

errors with the module assistant include /usr/src/modules/alsadriver/drivers/serialmidi.c:317: error 'struct tty_struct' has no member named 'atomic_write'

same message c:322,339
then make[6]: *** [/usr/src/modules/alsa-driver/drivers/serialmidi.o] Error 1
make[5]: *** [/usr/src/modules/alsa-driver/drivers] Error 2
make[4]: *** [/usr/src/modules/alsa-driver] Error 2
make[3]: *** [modules] error 2
make[3]: Leaving directory '/usr/src/linux-headers=2-6.17-11-generic'
make[2] *** [compile] Error 2

will try the module assistant again but I think it will error out again
Any thoughts?

---

### Post by jdfreshwater on 2007-03-13
I have one of these old dell machines, was previously a workstation for some company.  The thing about the built in sound card, is that it does not seem to like linux. I have tried many different distrobutions and it did not work on any of them.  Instead I went out and purchased a low end soundblaster card.  It may be worth investing in a cheep or old sound card to get sound working.

---

### Post by grandsatrap on 2007-03-13
I have the same problem. Everything (all of my devices) work fine in Ubuntu, but there is no sound! (It is the same Crystal pnp audio system codec ...). It shows up in the devices application as "crystal semiconductor CS423x sound" ...

Ubuntu is still a lot slower than the same computer running Win98SE (installed for over 3 years, so the registry is not as neat and small as it was). 
There are so many pages which have tweaks to speed up Ubuntu. I don't know how many are safe and/or effective! sigh!

---

