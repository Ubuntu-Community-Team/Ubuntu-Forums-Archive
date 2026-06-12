---
title: "Live CD 6.10 installation fail on sony laptop"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by scottnoakes on 2007-03-06
Hi,

I've got a Sony Vaio Laptop PCG-FX103 which I have replaced the HD on and the Windows ME  recovery disk will no longer work due to this change.

I would like to install Ubuntu however am having no luck so far. I've tried most things mentioned on the basic CD boot intro help screen. It looks like the installer is failing to detect the graphics card correctly, stopping after 30secs with a multi coloured 'snow' display on the screen.

I've tried booting from the boot: command prompt as mentioned:

boot: live vga=771 noapic nplapic  

But again no success. I have found a page which indicates that installing linux on this model is possible [http://cwrose.de/vaio/fx101.html](http://cwrose.de/vaio/fx101.html) 

How do I specify it to boot using the Intel i815EM i810 (X11) graphics chipset? What should I do now?

Help! Thanks Scott.

---

### Post by Kateikyoushi on 2007-03-06
I would recommend the alternate CD's text mode installation, and after install configure the machine.

---

