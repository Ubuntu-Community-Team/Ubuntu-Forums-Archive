---
title: "Trying to install tidev-modules"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by tac-tics on 2007-04-29
Hello, I'm trying to install the tidev-modules so I can toy around with developing for my TI-83+, but I'm having issues getting the driver compiled. For reference, I have the usb "silver link."

I have tried this a few different ways, but nothing works. It doesn't help I know almost nothing about how the kernel or modules work.

I have the tidev-modules package installed (which is just the source). I also have the linux-headers and the linux-source packages installed. I've tried 'make menuconfig' and 'make modules' on the source and headers to get them ready for the tidev-modules package. However, no matter what, I always run into problems. I've walked through all the steps in the README file, but I still can't get anywhere. 

Can someone please point me in a direction where I can figure out how to do this?

---

### Post by jfinkels on 2007-05-06
> **tac-tics said:**
> Hello, I'm trying to install the tidev-modules so I can toy around with developing for my TI-83+, but I'm having issues getting the driver compiled. For reference, I have the usb "silver link."

I have tried this a few different ways, but nothing works. It doesn't help I know almost nothing about how the kernel or modules work.

I have the tidev-modules package installed (which is just the source). I also have the linux-headers and the linux-source packages installed. I've tried 'make menuconfig' and 'make modules' on the source and headers to get them ready for the tidev-modules package. However, no matter what, I always run into problems. I've walked through all the steps in the README file, but I still can't get anywhere. 

Can someone please point me in a direction where I can figure out how to do this?

Perhaps if you tell us a specific error message that you get, we could help you out.

Are you following the instructions at /usr/share/doc/tidev-modules-source/README.Debian ?

---

