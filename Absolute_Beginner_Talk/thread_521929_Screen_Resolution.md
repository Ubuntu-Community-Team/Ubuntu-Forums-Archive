---
title: "Screen Resolution"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by rcdegges on 2007-08-09
Hi. I just bout a new Dell Inspiron with Ubuntu preinstalled. I have a 24" dell monitor that I bought with it, but for some reason, the "Screen Resolution" program won't let me change the resolution to the highest I can... It only has 3 presets atm. Can anyone tell me how to get it to the max resolution? Not 1280x1024...

---

### Post by ericesque on 2007-08-09
ran into this last night.   

In terminal

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

enter your password at promt

it will give you a graphical x-org configuration utility.  At the first screen  select the VESA driver.  

Than it will give you options for screen resolution.  Move the red cursor to your native monitor resolution and press SPACEBAR to select that resolution.  Tab over to OK.

Press  Ctrl+Alt+Backspace  (not delete)  to restart X  (the screen will go black then come back up)

Then go to your normal route to select your native screen resolution.

---

### Post by mswa03 on 2007-08-14
this worked! thanks a ton... my screen looks MUCH better now :)

---

