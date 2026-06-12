---
title: "help using &quot;make&quot; command for printer driver"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by onearmedpanda on 2007-07-31
i followed the instructions for installing a printer driver for my laserjet 1000 (the driver is foo2zjs) and when i cd to the directory and type make like it says i get this: 

#
#Dependencies...
#
             ***
             *** Error /usr/incude/stdio.h not installed!
             ***
             *** Install Software Development (gcc) package
             ***
make: *** [all-test] Error 1




so what do i have to install?
i have gcc, so i don't know what i'm missing
plus i went toe /usr/include/ and i saw some  folders, not individual files, so maybe i have stdio.h, its just no in /usr/incude/? i don't know, any help would be great, thanks

---

### Post by nitro_n2o on 2007-07-31
```
sudo apt-get install build-essential
``` :)

---

### Post by onearmedpanda on 2007-07-31
thanks for the quick reply
but i did that
and i got this message:


E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavaliable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by beathan on 2007-07-31
Make sure you don't have Synaptic open when running apt-get from the command line. It will give you that message otherwise.

---

### Post by nitro_n2o on 2007-07-31
basically close anything related to software downloads or software updates

---

### Post by onearmedpanda on 2007-07-31
thanks that worked and the printer driver is installed :)

---

