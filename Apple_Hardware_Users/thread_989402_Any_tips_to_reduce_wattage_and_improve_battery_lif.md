---
title: "Any tips to reduce wattage and improve battery life ?"
date: 2008-11-21
forum: Apple Hardware Users
---

### Post by anando on 2008-11-21
Hi

I have a macbook pro (1,1). When I run powertop I see around 16-17 W of power usage on an idle laptop. This is after I tried the various stuff suggested by powertop. 

I understand every laptop is different and there is no one size fits all solution to the question of reducing power usage.

But nevertheless, it would be good to compile tips/tricks that people have used in the past to improve the battery life of macbookpro with intrepid ibex. 

I'd be grateful for your suggestions which I could try on my laptop.

Regs,
Anand.

---

### Post by volanin on 2008-11-21
I have a Macbook 2,1 with Intrepid Ibex 64-bit.
From experiment, the things that consume most watts are:

- The display brightness.
- The wireless device.
- The iSight camera.

With maximum brightness and the modules loaded, I get an average of 19.5W
With minimum brightness and the modules unloaded, I get an average of 11.9W

So, if battery is a priority, lower your screen brightness and:
[b]$ sudo rmmod ath9k
$ sudo rmmod uvcvideo[/b]

There can be a few extra watts to be gained by following powertop
suggestions, and disabling bluetooth and sound, but since these watts
amount to an average of only 0.5W, and since disabling these devices
is a little harder (because there are processes keeping them on all
the time, forbidding you to remove the modules)... I usually
don't bother with these.
:)

---

