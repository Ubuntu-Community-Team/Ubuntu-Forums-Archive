---
title: "lm-sensors what am i doing wrong?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by JParkus on 2008-02-23
i am just tryn to use the funny looking guages in screenlets but cannot get lm-sensors working right 

here is some of what ive tried

parkus@ubuntu:~$ cd /usr/share/lm-sensors
parkus@ubuntu:/usr/share/lm-sensors$ sudo ./mkdev.sh
sudo: ./mkdev.sh: command not found
parkus@ubuntu:/usr/share/lm-sensors$ ## i have put the file in this folder
parkus@ubuntu:/usr/share/lm-sensors$ ## i have also rebooted
parkus@ubuntu:/usr/share/lm-sensors$ sudo modprobe via686a
parkus@ubuntu:/usr/share/lm-sensors$ sudo modprobe eeprom 
parkus@ubuntu:/usr/share/lm-sensors$ sudo modprobe i2c-viapro
parkus@ubuntu:/usr/share/lm-sensors$ sudo modprobe i2c-isa
parkus@ubuntu:/usr/share/lm-sensors$ sensors - detect
Parse error in chip name `-'
Try `sensors -h' for more information
parkus@ubuntu:/usr/share/lm-sensors$ sensors - d
Parse error in chip name `-'
Try `sensors -h' for more information
parkus@ubuntu:/usr/share/lm-sensors$ ##??


I did the module probe befor reboot
i know that i have the sensors because they work with the watermark screenlet

---

### Post by forestpixie on 2008-02-23
try doing this first

sudo sensors-detect

then reboot and it should work

---

### Post by JParkus on 2008-02-23
that did the trick now i need to know if anyone has got the temp guage working for manometer

---

