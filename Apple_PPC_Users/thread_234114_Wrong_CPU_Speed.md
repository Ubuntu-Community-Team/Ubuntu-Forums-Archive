---
title: "Wrong CPU Speed"
date: 2006-08-11
forum: Apple PPC Users
---

### Post by Shigun on 2006-08-11
Ok, I have a 900MHz G3 iBook.  However, im seeing 400MHz.  What gives, where are my 500MHz?

---

### Post by TuxCrafter on 2006-08-11
Check there for any cpu scalers.

cat /sys/devices/system/cpu/cpu0/

try to echo the max speed in the setspeed file.

---

### Post by Shigun on 2006-08-11
Yea, im seeing 2 values, 400000 and 900000.  I have not noticed many issues on the 400MHz setting;  What would be the benefits on a Linux based environment laptop to bump up to the 900MHz setting?

---

### Post by TuxCrafter on 2006-08-11
It is power saving if you neeed more cpu power it goes to the 900 if it works. Do some cpu hard stuf and 

cat /proc/cpuinfo

i have to go to work now so i cant repont soon bye.

---

### Post by Shigun on 2006-08-11
Alright, well thank you for your help,  Much appreciated =D

---

