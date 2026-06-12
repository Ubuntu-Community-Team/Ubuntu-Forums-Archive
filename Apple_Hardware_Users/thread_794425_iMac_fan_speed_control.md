---
title: "iMac fan speed control"
date: 2008-05-14
forum: Apple Hardware Users
---

### Post by oli1978 on 2008-05-14
Hi all,

I installed today Hardy 8.04 on my iMac. Everything went fine. However, I would like to speed up the HDD fan, because this one is very hot (about 65°C when doing nothing). I used some tutorials, but, when I do ```
pwmconfig
``` I always get ```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```.
I also tried ```
sudo modprobe applesmc
```, but this time I get ```
FATAL: Error inserting applesmc (/XXX/XXX/applesmc.ko): No such device
``` whereas the file exists though.

I really need some help. Do you have any issue ?

Best regards,

Olivier

---

