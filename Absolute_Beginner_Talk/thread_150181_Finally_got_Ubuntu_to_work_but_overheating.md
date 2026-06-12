---
title: "Finally got Ubuntu to work but overheating"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by xXx 0wn3d xXx on 2006-03-25
Hi, I finally got X to work and installed Ubuntu in 30 min :) Now I have a problem: My fans don't seem to be working... what can I do ? I don't want to overheat my system. It is getting very hot and I can't feel any air comming out of the vents. Any way to fix this ?

---

### Post by rfruth on 2006-03-25
Desktop or notebook, where in the world are you, whats the average temp / humidity level ?

---

### Post by xXx 0wn3d xXx on 2006-03-25
It's a Gateway Laptop, I'm in the US It's like 40 + raining outside It's about 65-70 in my house. Maybe it's b/c I'm charging the battery but I haven't heard the fans come on.

---

### Post by Panhead Bill on 2006-03-25
Most laptops vary the fan speed from 0  to maximum rpm as needed to conserve battery power.  If you can get into the laptop's utilities, there may be a temp monitor that will let you know where your CPU is at.

If you start running a heavy cpu use application, (maybe with lots of graphics?) the fans should cycle on.  

I don't think your OS would have any effect on the fan control built into your laptop.  (I'm inferring from your original question.)

---

### Post by xXx 0wn3d xXx on 2006-03-25
ok is there an automatix for AMD 64 ?

---

### Post by sn123 on 2006-03-25
[QUOTE=MasterChief1234]Hi, I finally got X to work and installed Ubuntu in 30 min :) Now I have a problem: My fans don't seem to be working... what can I do ? I don't want to overheat my system. It is getting very hot and I can't feel any air comming out of the vents. Any way to fix this ?[/QUOTE]

What's the temp. that Linux is reporting when you feel it's overheating? On my Intel Centrino it generally ranges between 40-50 deg. celcius with or w.o. fan running.
```

$ sudo acpi -V

```

S

---

### Post by trent dillman on 2006-03-25
Well, MasterChief, I am very happy to hear you got your Ubuntu install working!

---

### Post by nalmeth on 2006-03-25
Automatix does not support amd64. The following link will show you how to make a 32-bit environment inside the 64-bit installed system, and is less complicated than it looks (if you do it, make sure EVERY instance of HOARY is changed to BREEZY), also it is safe to install the generic i386 (32-bit) version on a 64-bit processor, in fact it worked better for me.
[SIZE=-1][COLOR=#008000]www.**ubuntu**forums.org/showthread.php?t=24575
[/COLOR][/SIZE]

---

