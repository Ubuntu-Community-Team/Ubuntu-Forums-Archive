---
title: "Boot and suspend pommed brightness issues"
date: 2009-09-13
forum: Apple Hardware Users
---

### Post by tohvanah on 2009-09-13
So the entire reason I am using Ubuntu on my MacBook 1,1 is that the logic board is damaged and always believes the lid is closed. I was on 7.10 running well, but without suspend. Under 7.10 the backlight would be off on boot until the user was automatically logged in, then (pommed i assume) kicked in and the backlight came on. Fn keys worked normally.

I've upgraded to 8.04. Now upon boot or resume, the backlight is off. Fn keys DO work to turn it on. A command line fix for this using vbetools dpms on, doesn't work. dpms on/off does nothing until the brightness is brought out of 0. 

Is there any workaround? I've altered pommed.conf to max values for all 3 initial brightness settings. Can pommed/the brightness be altered via terminal?

Thanks!

---

