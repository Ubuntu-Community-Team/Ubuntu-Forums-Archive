---
title: "my mac is really really hot..."
date: 2008-07-14
forum: Apple Hardware Users
---

### Post by Oscar Pradilla on 2008-07-14
Hi again, i'm worry about this, my mac runs very hot, i've installed the hardware sensors and the fans are over >5000 rpm to keep it at 38C, the next temperatures shows 98C, the aluminium is really hot, almost hurts..

I've done already the manual fan speed config, but they runs auto faster than the 5000rpm at fan speed3.

Would this damage my mac? why so much heat? Does anyone solved this problem...

Tks

---

### Post by articpenguin on 2008-07-15
what mac? what processor?

---

### Post by alfalfa31 on 2008-07-15
If it's an "Air" then welcome to light thin world.  The whole laptop is a heatsink.  It's too thin to have anything other than the case as a sink.

---

### Post by Oscar Pradilla on 2008-07-15
Macbook pro (intel core duo) 17 inch, 2gb ram

---

### Post by coreofreeality on 2008-07-15
generally, semiconductors can take about 125 celsius before they give up, and most processors these days have thermal shutdown protection.

its still not good to have it running that hot though.

---

### Post by Oscar Pradilla on 2008-07-15
what i've reading about that tells me that is a malfunction of ubuntu, a lot of laptop not only macbook has this issue, i'm trying some configs that have been post to see if i can keep it down...hope...if not...i'm not gonna risk my MBP and go back to my old OS.

---

### Post by kosumi68 on 2008-07-15
The whole macbook series is running hot. Unless the interplay between cpu frequency, cpu temperature, hdd temperature and fan speed is taken into account, it simply will not work properly. This means the default frequency module in ubuntu, powernowd, is not good enough for these machines. At large, aiming at a cool and quiet experience with any laptop, there should really be a better default option.

Here is how I keep my MBA reasonably cool:

1) Use powernowd with the "-m 2" option

2) Use the powersave governor

3) Turn down the screen brightness whenever I can

4) Use laptop_mode also when on power (just make sure your disk does not spin down)

Right now, powertop says I am using 11.5 watts. The lower power consumption, the cooler your machine will be. And the battery will last longer :)

---

