---
title: "wireless connection"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by pacco on 2007-03-03
i have an older laptop runnin ubuntu server 6.06,and during the installation the card works fine after i mannually configure it,but after everything installs,it won't work and since there is no gui on the server i don't know what command to use to get it started.

I can't even log in as root to change the files.
Any help would be appericiated,

Thanks in advance
:)

---

### Post by tgalati4 on 2007-03-03
ifconfig and iwconfig will give you some status information.

You should log in as a regular user and use

sudo ifconfig ... and sudo iwconfig . . .

to change settings.

---

### Post by pacco on 2007-03-03
i tried bot those commands and got a no such device error
it has my device as ath0,but i don't really know which command to use to see if it is ath0,eth0,etc

Thank You
:)

---

### Post by tgalati4 on 2007-03-04
Try:

ifconfig

and

iwconfig

to view settings.

sudo ifconfig and sudo iwconfig to change settings.

---

### Post by pacco on 2007-03-04
ok, i tried that and it says that my wireless is sit0 instead of ath0?

i have a netgear pci card that slides into the laptop

---

### Post by tgalati4 on 2007-03-05
In a terminal, post the output of:

lspci

Perhaps there is an interrupt conflict with the pcmcia card (typically interrupt #11).  Try turning off the serial port, USB ports, parallel port in BIOS and see if networking works.  Then turn those devices back on one at a time.  Don't forget to turn OFF Plug-N-Play operating system in BIOS as well.

Good luck.

---

