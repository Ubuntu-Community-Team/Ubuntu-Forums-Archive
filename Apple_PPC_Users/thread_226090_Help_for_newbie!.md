---
title: "Help for newbie!"
date: 2006-07-30
forum: Apple PPC Users
---

### Post by cosmonaut on 2006-07-30
Hi everyone,

I've just successfully installed Ubuntu on my 1.33 GHz G4 Powerbook and so far am very impressed.

BUT where is the hash key #

I'm trying to do some coding to reduce the temperature at which the fan kicks in but need the # key :confused: 

I've searched the forums and google etc but nothing (well, apart from people who mention in passing that they've discovered how to type # but don't elaborate any further :sad: 

Any advice welcome!

---

### Post by rasec on 2006-07-30
I'm confused. Why do you need # to change the fan thresholds?

To change the fan thresholds on my powerbook, I would just modify limit_adjust in /sys/devices/temperatures. Keep in mind that limit_adjust is an offset to the current fan threshold, so giving it a negative value will lower the fan threshold, while a positive number will raise the threshold. If you go into that directory, you'll see a couple sensorX_fan_speed _limit and _location files, those files should tell you everything you want to know about your powerbook temperature status. One last note, all of the files in the temperature directory work in Celsius.

---

### Post by linear on 2006-07-30
I'm confused too. Isn't it where you'd normally find it? (for example, on a US keyboard layout it's shift-3.)

---

### Post by cosmonaut on 2006-07-31
Thanks for that. My keyboard is a UK one and I get # by typing alt and 3 (under mac OS X). When I try this in Ubuntu I only get a 3.

---

