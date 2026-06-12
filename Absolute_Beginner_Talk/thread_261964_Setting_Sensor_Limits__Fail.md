---
title: "Setting Sensor Limits  Fail"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by ramjet_1953 on 2006-09-21
When Ubuntu is booting I get a "Setting Sensor Limits  Fail" warning.
Is this to do with monitoring temperatures, etc?
If so, how do I correct it?

Regards,
Roger :cool:

---

### Post by jordanmthomas on 2006-09-21
```
sudo apt-get remove lm-sensors
```
I have the same problem on boot-up, but I am too lazy to fix it.  The error is harmless, though, if you want to keep lm-sensors.
What kind of computer do you have?  Just curious, because there may be something else you can install if you want to monitor temperatures.

---

### Post by ramjet_1953 on 2006-09-21
I have an Acer TravelMate 4101.
It has a Pentium M730 processor (1.6Ghz) and the Intel 915 Graphics chipset.

Regards,
Roger :)

---

### Post by jordanmthomas on 2006-09-21
That's the same processor / graphics I have.
I think it would probably just be best to remove lm-sensors or just deal with the error.

(Had you had a Dell, I might have suggested to install i8kutils, but I don't figure that would work on your computer)

---

### Post by stimpyaw on 2007-01-28
The "settings sensor limits fail message was bugging me too. I'm a newbee to Ubuntu Linux I wasn't sure how to fix that issue.  But I did a search in the forms and found the answer "sudo apt-get remove lm-sensors" and it worked. 

Thanks jordanmthomas!

---

