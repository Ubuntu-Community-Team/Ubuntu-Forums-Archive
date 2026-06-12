---
title: "NEW LAPTOP! Fan Question"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2007-05-29
I am currently running an HP Pavilion dv9000 with Core 2 Duo, and have a few questions...

I just got my brand new laptop, and everything seems to be working a LOT better than on my old desktop PC.
I Have a few questions though..

1) acpi -V displays:
ubuntu@ubuntu:~$ acpi -V
     Battery 1: charging, 7%, rate information unavailable.
     Thermal 1: ok, 22.0 degrees C
  AC Adapter 1: on-line

Is it safe to assume that my fan will turn on when the computer gets hot?
(since on Vista; my computer gets EXTREMELY hot, and I was wondering if there was a way to have it turn on the fan if it gets above... 70 degrees C?  Would this be a good temp to set it to?)

2) How can I tell if i'm taking advantage of both cores?

---

### Post by Sparkster185 on 2007-05-29
70 degrees C would probably fry your CPU.  You probably mean 70 F, I'm guessing....

My laptop is pretty new (Toshiba Satellite A135 series) and the fan turns on automatically (running Feisty).

---

### Post by chris062689 on 2007-05-29
How can I set / tell the laptop what temperature to turn the fan on at?
What do you say would be a good temp in F to turn on the fans?

(How can I get it to display in F instead of C?)
I'm running the Live CD right now

---

### Post by annda on 2007-05-29
Q2: the easiest way to see your processor(s):

```
cat /proc/cpuinfo
```

or go to system>preferences>hardware information

---

### Post by silkstone on 2007-05-29
Go into Synaptic and install the sensors-applet package. That will allow you to display the temperature(s) of the processor core(s) on the top panel so you can keep an eye on them.

My laptop - Acer 5612 with Centrino T2300 - stabilises with both cores at around 45C. The fan speeds up a little if either core goes over 55C. The processor is designed to run up to 80C but it has a thermal shut-down at about 70C. Even under intense use it has never gone above 60C.

Occasionally Ubuntu will mis-read the sensors on boot-up and will show one core at over 70C and the other at about 25C. I think it's adding two together. The fan then runs full-speed. I have to restart Ubuntu to fix this.

---

