---
title: "SD card reader problem"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by Frank Golden on 2006-06-05
Hi Folks;
   Have a very stable copy of Ubuntu 6.06LTS on my Acer Aspire as5672WLMi
notebook. Every thing works well except the built-in Texas Instruments
PCIxx12 Integrated Flash Media Card Reader. It is listed in Windows ( I have a dual boot setup with XP Pro) as a PCMCIA and flash memory device.
It doesn't appear to be recognized by Ubuntu. Does anyone know of a driver download or install that I could use to make this device useful in Ubuntu?

---

### Post by Frank Golden on 2006-06-08
thanks for the help

---

### Post by annotei on 2006-09-05
hi !
I use one driver that can be found at : [http://developer.berlios.de/projects/tifmxx]("http://developer.berlios.de/projects/tifmxx")

There are 3 modules to compile (a simple make)
Then copy them into /lib/modules/`uname -r`/misc.
Finally, a *sudo depmod -a* updates the module database
You can load them with modprobe

Antoine.

---

