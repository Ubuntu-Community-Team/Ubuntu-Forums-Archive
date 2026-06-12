---
title: "not working plz help"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by inmate#001 on 2006-08-12
when i put in the desktop CD and click install it starts then goes to a splash screen where it stops at adding live CD user then it goes to a text screen that reads
uncompressing linux... Ok, booting the kernel.
[17179746.500000] Buffer I/O error on device hdd, logical block 293222
[17179751.264000] Buffer I/O error on device hdd, logical block 293224
[17179755.680000] Buffer I/O error on device hdd, logical block 293226
[17179764.256000] Buffer I/O error on device hdd, logical block 293184
[17179766.320000] Buffer I/O error on device hdd, logical block 293184

at this point the computer stops doing anything on this screen i can enter text but i dont know if it does anything

thanks for the help
inmate

---

### Post by louis_nichols on 2006-08-12
hm... that looks to me like it can't read a certain part of the cd. Did you try a media check? Or you can directly try re-burning the image on another CD and try the install again.

---

### Post by inmate#001 on 2006-08-12
wouldnt hdd be hard drive but then i have the same problem on all the couputers i tried it on so it is probably the cd

---

### Post by louis_nichols on 2006-08-12
"hdx" refers to IDE devices, so "hdd" doesn't come from "harddisk". It's just the secondary IDE slave. hda is the primare IDE master, hdb primary IDE slave and hdc secondary IDE master. And so on, I suppose, although I don't know how many motherboards support more IDE devices.

---

### Post by inmate#001 on 2006-08-12
so then hdd could be refering to the cd drive

---

### Post by louis_nichols on 2006-08-13
It almost certainly does. Just burn a new cd and you'll be alright. ;)

---

