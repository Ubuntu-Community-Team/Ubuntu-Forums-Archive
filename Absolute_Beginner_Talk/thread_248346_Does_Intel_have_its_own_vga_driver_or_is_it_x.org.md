---
title: "Does Intel have its own vga driver or is it x.org?"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by yasoumalaka on 2006-08-31
I was just wondering because google earth gets all messed up looking and I was wondering if I need a better vga driver. Thanks.

---

### Post by jordanmthomas on 2006-08-31
What kind of card do you have, specifically?
It should be listed here:
```
 lspci | grep Display
```

---

### Post by yasoumalaka on 2006-09-01
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)

---

### Post by jordanmthomas on 2006-09-01
That's the same card I have! 

3D should generally work out of the box.  Do your 3D screensavers work?

If so, here is what I had to do to get Google Earth to display correctly.  
In a terminal, type this:
```
LD_PRELOAD=/usr/lib/libGL.so.1.2 
googleearth
```

This should work.  If it does, you can modify your googleearth startup script.
From your home directory in a terminal, type
```
gedit googleearth
```
and after the first comments (lines that start with a #) put this:
```
export LD_PRELOAD=/usr/lib/libGL.so.1.2
```
Worked for me at least...

---

