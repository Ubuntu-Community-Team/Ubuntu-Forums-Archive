---
title: "How to change vrefresh with ati"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-09-24
Does anyone know the command to set the refresh rate to your moniter with the ati driver?

---

### Post by Perfect Storm on 2006-09-24
Have you tried adding/changing it in your xorg.conf?

---

### Post by WalmartSniperLX on 2006-09-24
no i havnt how do I do that?

---

### Post by Perfect Storm on 2006-09-24
Firstly, find your monitor specs (by manual or on the web). You are looking for the numbers for:
Horizontal scan range 
Vertical scan range

When found, open the xorg.conf

```
sudo nano /etc/X11/xorg.conf
```

find the **Section "Monitor"**

and change your 
HorizSync 
VertRefresh

to the what fits your monitor.
save <ctrl> + <o> and exit <ctrl> + <x>

restart X


eg. mine looks like this:
HorizSync 30 - 107
VertRefresh 48 - 170
for Dell p992 monitor

---

### Post by WalmartSniperLX on 2006-09-24
Ok thanks

---

