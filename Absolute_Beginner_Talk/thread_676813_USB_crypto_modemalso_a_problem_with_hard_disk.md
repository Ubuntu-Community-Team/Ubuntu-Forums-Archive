---
title: "USB crypto modem/also a problem with hard disk"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by souraklis on 2008-01-24
I have installed ubuntu but i have some problems with connection to internet. I have usb modem and i cant connect to internet. Furthermore i have installed Ubuntu in a ATA hard disk driver and  the O.S  takes long time to  log in. Also all the process of the system are crashed. What can i do from that?

Can i find codecs and pluggins in the windows from ubuntu players?

---

### Post by Paulmd on 2008-01-25
> **souraklis said:**
> I have installed ubuntu but i have some problems with connection to internet. I have usb modem and i cant connect to internet. Furthermore i have installed Ubuntu in a ATA hard disk driver and  the O.S  takes long time to  log in. Also all the process of the system are crashed. What can i do from that?

Can i find codecs and pluggins in the windows from ubuntu players?

Let's start in order of the worst problems first. "Also all the process of the system are crashed."

This does not sound good. As this may indicate problems with your hardware. If your hardware doesn't work, don't expect your software to.

DIAGNOSE your system. Check the ram with memtest86+ (available on your installation cd). Check the hard disk with the tool supplied by the manufacturer of your hard drive, If you don't know who made your hard drive, and are too lazy to find out, you can use Seatools, which is distributed by Seagate.

Also, check your installation cd for errors. You get an option to do this when you boot the cd.

Next up: the usb modem. I regret that dialup modems and linux are not the best of friends. In order to effectively help you, I need to know the make and model of your modem, so I can research the availability of drivers for it.

In order to answer the question "why does login take so long?" I need to know the specs of your system. How much ram do you have, and how fast is your processor? And how much time exactly is a long time?

With regard to codecs, they are available from the Ubuntu repositories, which are available in the synaptic package manager. PROVIDED you can get your system online.

---

