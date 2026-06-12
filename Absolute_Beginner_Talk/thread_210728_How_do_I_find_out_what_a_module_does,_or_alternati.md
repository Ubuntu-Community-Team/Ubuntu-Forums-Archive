---
title: "How do I find out what a module does, or alternatively which is loaded for a device?"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by jonboy99 on 2006-07-07
Am having trouible identifying which module is being loaded for my wireless card.  (wireless forum rather quiet at the mo)

I can get a list of modules with lsmod, but don't know what they all do as the names don't give much away.

Is there a command which will give me the function of each one, or a list somewhere.

man will work for some but not many.

Cheers
Jon

---

### Post by Dr. Nick on 2006-07-07
Are you trying to find out what driver is loaded for your wireless or somehing?

If it is a usb wireless card have a look at the usbcore line. 

If you want to get a general idea of what type of hardware a module is for then open a terminal and type

**locate *module*** and look at the results from /lib/modules/2.6.15-21-386/kernel/drivers/
to get a general idea of what the module is for. Thier are no websites that list what every module does that I know of.

---

