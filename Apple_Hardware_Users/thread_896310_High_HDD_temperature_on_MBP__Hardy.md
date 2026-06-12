---
title: "High HDD temperature on MBP / Hardy"
date: 2008-08-21
forum: Apple Hardware Users
---

### Post by i_ll_be on 2008-08-21
Hello all,

I have been using hardy on my MBP 1.1 for 2 months now. I find the temperature higher than in OSX (especially in the HDD area, left from the trackpad). I don't care about battery life as it is dead for months, but I care about heat / noise.

I set the minimum fan speed to 3000rpm, my core temperature is around 59-60 degrees (sensor 5 in sensor-applet). For the same fan speed in OSX, it is about 53-54 deg (from smc fan control).

Do you have any advice ?

I understand that the hardware management is not as good as in OSX, but I am surprised to see a big difference in the HDD temperature (when typing in ubuntu, the front cover over the HDD is so hot that it is not comfortable.

By the way, do you know the detailed locations (physically in the machine) of the sensors in the sensor-applet ?
Also which sensor is used for temperature display in SMC fan control ?

Thanks for your help !

---

### Post by cyberdork33 on 2008-08-21
It could be that the set rpms are not accurate. try bumping the fan speed up a little in Ubuntu until you have a similar reading in both and note the difference in rpms. Then you can experiment with setting them to different levels and determine if the set rpms are always just that much apart.

It could also be that OSX powers down the hard drive much more agressively than Ubuntu when it is not being used.

IDK about your machine specifically, but in my iMac, it literally has a little circuit board attached to the side of the hard drive with some really sticky double-sided tape. This as a small cable that connects to the mainboard. The actual CPU should have two sensors built-in (one for each core). I am unsure of others.

---

### Post by i_ll_be on 2008-08-21
Hello,

Thanks for your answer !

I checked more closely and actually the HDD temperature is about 43 deg, even after keeping the machine idle for a while.

When you say "OSX powers down the hard drive much more agressively than Ubuntu when it is not being used", do you think it is easily possible to implement such a thing in Ubuntu ?

Anyway I am not very optimistic, because the opening of applications, launching of video encoding does not impact the hdd temperature. Maybe there is no other way than increasing the fan speed (and increasing the volume in Rythmbox to cover it ! :lolflag:)

---

### Post by cyberdork33 on 2008-08-21
> **i_ll_be said:**
> When you say "OSX powers down the hard drive much more agressively than Ubuntu when it is not being used", do you think it is easily possible to implement such a thing in Ubuntu ?
Look into laptop-mode

---

### Post by i_ll_be on 2008-08-24
I have finally bought a coolpad, which lowers the temperature by 5 deg (both CPU & HDD).

I just noticed one thing : when using FF 3.0, if the website has a lot of flash, then the temp increases a lot (nearly 10 deg) >> tested on [www.sports.fr](www.sports.fr)

---

