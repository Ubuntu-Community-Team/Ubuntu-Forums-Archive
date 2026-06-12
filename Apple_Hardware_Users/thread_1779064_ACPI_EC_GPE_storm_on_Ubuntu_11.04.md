---
title: "ACPI: EC GPE storm on Ubuntu 11.04"
date: 2011-06-09
forum: Apple Hardware Users
---

### Post by BadLongUserName on 2011-06-09
HI Everyone.

Someone is getting this kind of error?  I think this is related to some problems I've been having on Ubuntu 11.04. My Macbook 6,1 just freezes and remains turned on and repeating whatever it is doing when it happens (plays sound in loops and such). 

It seems it was detected in previous versions but it was supposed to be corrected, but I couldn't manage to locate a fix.

---

### Post by Sloth on 2011-06-10
Had this on my iMac.  Was only able to solve it by finding the gpe interrupt that was storming the system (IIRC, by cat'ing /sys/firmware/acpi/interrupts/gpe* and seeing which one was going wild.)

Then, in /etc/rc.local, I added this:

echo "disable" >/sys/firmware/acpi/interrupts/gpe13

As, in my case, gpe13 was the offending interrupt.

---

### Post by BadLongUserName on 2011-06-10
Thanks Sloth! I will be certain to check it out and return here with the results!

---

### Post by BadLongUserName on 2011-06-11
Oh... I got a lot of "invalid" entries, but nothing looked like wild. What should I be looking for?

---

