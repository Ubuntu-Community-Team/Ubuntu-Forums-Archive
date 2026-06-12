---
title: "Notebook temperature"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by shareMenaPeace on 2007-02-06
Hi, 
im new to linux and notebooks so im not sure which temperature is ok and when it starts to become critical?

acpi -t 
 [HTML] 
     Thermal 1: ok, 52.0 degrees C
[/HTML]

Is this just fine?
Are there things i can do to throttle the temperature? 

Thx for some hints.

---

### Post by amohanty on 2007-02-06
It sort of depends on your cpu. Take a look for 'normal' operating temps:
[http://www.heatsink-guide.com/content.php?content=faq.shtml](http://www.heatsink-guide.com/content.php?content=faq.shtml)
Keep in mind this is all relative.

As to what you can do about it, I would sugeest google with your laptop model and cpu as search criteria.

HTH
AM

---

### Post by shareMenaPeace on 2007-02-06
ty

---

### Post by kerry_s on 2007-02-06
You have to tell us what cpu you have, if you want help with it.
athlon= athcool
pentium=cpudyn,cpufreq,> i think

---

### Post by shareMenaPeace on 2007-02-06
Intel® Centrino®  Duo-Prozessor CoreTM   945 GM

From lspci
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)


Searching but didnt found yet the max temperature...

i guess i have to contact intel?

From the link 
> Intel Pentium 4, Pentium 4 Extreme Edition, Pentium M
Pentium 4
Max. temperature depends much on model and clockspeed, but no clear pattern is visible. Consult Intel's tech specs for information on your particular model.
(Lowest: P4 Extreme Edition 3.2GHz with 64°C, highest: P4 Willamette 1.8GHz with 78°C). 	64°C - 78°C
Pentium M
	100°C (!)

---

### Post by atihimself on 2007-02-06
Most of the notebooks can handle temperature 80-95 degrees,
right now i have 1.6 ghz pentium M and under heavy load temp goes up to 70-75c.
My older notebook works on 70-85c almost three years now, avarage uptime 5-7 days, then it gets slow and I have to reboot

---

### Post by shareMenaPeace on 2007-02-06
> **atihimself said:**
> Most of the notebooks can handle temperature 80-95 degrees,
right now i have 1.6 ghz pentium M and under heavy load temp goes up to 70-75c.
My older notebook works on 70-85c almost three years now, avarage uptime 5-7 days, then it gets slow and I have to reboot
Thank you this is a great info, cheers.

---

