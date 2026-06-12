---
title: "Logs me out everytime I move touchpad or mouse"
date: 2012-02-03
forum: Asus Ubuntu Support (CLOSED)
---

### Post by miaerbus on 2012-02-03
I'm using Asus K50IJ with Ubuntu 11.10, I upgraded from 11.04. It's been working perfectly the last few months. Today my laptop run out of battery, so I plugged it in and I turned it on again. But when I touch my touchpad, it suddenly log me out of the system and gives me the usual logout procedure (turning off apache2, etc) and after that new login splashscreen. I tried the USB mouse, and it happened the same thing. So now I can only use my keyboard. I turned off my touchpad (synclient TouchpadOff=1) because it got so annoying.

Does anyone have any idea how to fix this?

---

### Post by melchior2222 on 2012-02-04
Hey,

I've got precisely the same problem. Would be intrigued if you manage to find a solution.

Running Ubuntu 11.10. Running Gnome instead of Unity2D.
Still trying to solve the problem.

When I move the mouse, the screen shows the $root terminal briefly and then reboots into the Splash Login Ubuntu Screen. No matter what I do, each time I move the mouse I get this problem.


Adios

---

### Post by miaerbus on 2012-02-04
I solved it by removing Unity PPA.

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:unity-team/staging
sudo ppa-purge ppa:unity-2d-team/unity-2d-daily
```

---

### Post by melchior2222 on 2012-02-04
[SOLVED]
Thanks miaerbus that solved the problem.

---

