---
title: "Installation DVB"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by James Blunt on 2005-11-27
hi,

i'm using ubuntu 5.10, and I'm trying to install the driver for my tv
card (it's a avermedia dvb-T USB).

I've got kernel 2.6.12 on the system and I got stuck on
the very first step, when trying do 'make' in the dvb-kernel/build-2.6
folder. the message is: 

...
make -C /lib/modules/2.6.12-10-386/source
SUBDIRS=/home/dangn/devel/dvb-kernel/build-2.6 AV7110_FIRMWARE=
AV7110_OSD=y
make[1]: Entering directory `/lib/modules/2.6.12-10-386/source'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-10-386/source'
make: *** [all] Error 2


Please help, many thanks!

---

