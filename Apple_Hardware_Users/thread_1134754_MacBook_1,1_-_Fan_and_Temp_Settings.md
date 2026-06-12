---
title: "MacBook 1,1 - Fan and Temp Settings"
date: 2009-04-23
forum: Apple Hardware Users
---

### Post by bobisimo on 2009-04-23
I did some searching on measuring/adjusting fans and temp settings - and found information for other MacBook variants (like the MacBook Pro) but nothing for the MacBook 1,1.

I tried the information anyway (echo 3000 > /sys/devices/platform/applesmc.768/fan1_min) but got a permission denied.

There's nothing on the install page for MacBook 1,1 about fans and temperature. Does anyone have any information to help me out? Maybe it's silly, but I like seeing how fast the fans are running and how hot the laptop is running. I'd probably be fine with the default fan settings, but I'd still like the information. I just want to make sure my MacBook doesn't melt. :)

---

### Post by cyberdork33 on 2009-04-24
> **bobisimo said:**
> I did some searching on measuring/adjusting fans and temp settings - and found information for other MacBook variants (like the MacBook Pro) but nothing for the MacBook 1,1.
It is the same for all Intel Macs. There is no difference for specific models.

> **bobisimo said:**
> I tried the information anyway (echo 3000 > /sys/devices/platform/applesmc.768/fan1_min) but got a permission denied.
That is because this is essentially two different commands, and sudo only modifies the first one. Using 'tee' will help:
```
echo 6000 > sudo tee -a /sys/devices/platform/applesmc.768/fan1_min
```There are several threads on fan control here in the forum, and some people have written scripts that allow a little more flexibility in the fan control.

Here are a couple of examples.
[http://ubuntuforums.org/showthread.php?t=981280](http://ubuntuforums.org/showthread.php?t=981280)
[http://ubuntuforums.org/showthread.php?t=969183](http://ubuntuforums.org/showthread.php?t=969183)

---

### Post by bobisimo on 2009-04-24
Thank you so much for pointing me in the right direction and helping me. I appreciate it! :D

---

### Post by bobisimo on 2009-04-24
... double post, sorry

---

### Post by bobisimo on 2009-04-25
If I enter "sensors" on Ubuntu's terminal, I get something like:

[INDENT]Exhaust  :  3997 RPM  (min = 1500 RPM)

temp1:       +31°C
temp2:       +51°C
temp3:       +48°C
temp4:       +46°C
temp5:       +46.5°C
temp6:       +46.5°C
temp7:      +127.8°C
temp8:       +50°C
temp9:       +127.8°C
temp10:      +38.5°C[/INDENT]

If I view iStat Pro in Leopard, I get something like:

[INDENT]Exhaust : 1493 RPM

CPU A: +48°C
Battery 0: +30°C
Enclosure Bottom: +31°C
Heatsink A: +6°C
Heatsink B: +59°C
Mem Bank A1: +44°C
Northbridge 1: +44°C
Northbridge 2: +45°C
Hard drive: +33°C[/INDENT]

Does anyone know which labels apply to "temp1", "temp2", etc? I'm trying to figure out normal readings in Leopard so I can gauge whether I'm getting normal values in Ubuntu.

---

### Post by bobisimo on 2009-04-27
> **bobisimo said:**
> temp1: +31°C
temp2: +51°C
temp3: +48°C
temp4: +46°C
temp5: +46.5°C
temp6: +46.5°C
temp7: +127.8°C
temp8: +50°C
temp9: +127.8°C
temp10: +38.5°C

I just can't figure this one out...

I ran some tests (no load-to-very heavy load) in Leopard where I have temperature labels and I discovered the following ranges:

[indent]Exhaust: 1492 RPM to 6216 RPM

CPU A: +48°C to +89°C
Battery 0: +30°C to +31°C
Enclosure Bottom: +30°C to +35°C
Heatsink A: +6°C to +126°C
Heatsink B: +59°C to +80°C 
Mem Bank A1: +44°C to +56°C
Northbridge 1: +44°C to +63°C
Northbridge 2: +45°C to +65°C
Hard drive: +33°C to +37°C[/indent]

But if I look at the above temperatures in Ubuntu, only some of them match:

[indent]Exhaust : 3997 RPM

temp 1 = (+31°C) Battery 0
temp 2 = 
temp 3 = 
temp 4 = 
temp 5 =
temp 6 =
temp 7 = (+127.8°C) Heatsink A
temp 8 = 
temp 9 = (+127.8°C) Heatsink A, duplicated?
temp10 = (+38.5°C) Hard drive - or, maybe/possibly Enclosure Bottom?[/indent]

Temp 2, 3, 4, 5, 6, and 8 are all around the same range, from 46 to 51°C, so there seems to be no way to differentiate them. Additionally, only 5 items under Leopard would match the ranges. So we either have a duplicate or... ?

On the other hand, it would appear that the Ubuntu temperatures under 9.04 on my MacBook are VERY LIKELY well within the normal/healthy Leopard range. That speaks well for Ubuntu and reassures me a little bit in regard to my laptop's health and safety. I would like to do more testing on temperature ranges in Ubuntu but I want to figure out what correlates to what, first.

Thoughts?

---

### Post by bobisimo on 2009-05-05
I installed "hardinfo" and got a little more detail:

    * temp1: 54.00°C
    * temp2: 59.00°C
    * temp3: 57.00°C
    * temp4: 52.00°C
    * temp5: 54.25°C
    * temp6: 54.50°C
    * temp7: 67.25°C
    * temp8: 58.00°C
    * temp9: 71.00°C
    * tmp10: 43.50°C
    * temp1: 54.00°C
    * temp1: 54.00°C
    * FujHD: 36°C

The bad news is that some of the numbers are out of order in comparison with prior results (i.e. entering "sensors" into the terminal).

The good news is that I now have a HD reading, pre-labeled. Woo!

Also, temp1, in this list, is the CPU - since it is broken down by the two cores at the bottom and because I was able to get matching temperatures when entering "sensors" - where I actually get a labeled CPU reading. 

I believe 7 and 9 are still heat sinks since nothing else in Leopard climbs that high under general web browsing conditions. Temp 10 correlates to nothing that I can figure. I haven't seen the enclosure bottom or battery read anywhere close to that high of a temperature, nor have I seen anything else (mem bank, northbridge) read that low. So what's left?

So, in conclusion (ha), I think I'm giving up on effort to label the temps with the knowledge that:

1) the temp labels are different based on which program's readings are listed;
2) getting CPU and HD readings are easy, and they are within the same healthy range one might see while using Leopard in normal situations - aka Ubuntu 9.04 is not necessarily any different on the system than Leopard;
3) defining all the temp labels is impossible, for me, so giving Ubuntu a perfect pass/fail is also impossible. It definitely "feels" warmer on the bottom, and the fans seems to run a little faster/more often, but under default Ubuntu settings the laptop remains in healthy ranges and also is generally as quiet as under Leopard. The possibility that my battery is 10 degrees warmer than normal, for example, seems unlikely. So I'm not worried about using Ubuntu.

If anyone else has anything else to add, like something I could do to gain more labels or something, I would love to hear it!

---

