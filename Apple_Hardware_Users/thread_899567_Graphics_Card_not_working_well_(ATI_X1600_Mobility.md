---
title: "Graphics Card not working well (ATI X1600 Mobility)"
date: 2008-08-24
forum: Apple Hardware Users
---

### Post by goatchild on 2008-08-24
Hi guys,

I've just installed Ubuntu on my iMac (white intel core duo).
I've managed to get everything to work so far, except my graphics card:

When I move windows around or scroll down etc, I notice some twitching.
I've also installed two games, Castle Wolfnstein, and FlightGear. 
In castle wolfenstein I can's see a thing, except for the text, everything else is dark. In flightgear everything shows up weird, so I can't even play.

I've installed the proprietary driver for my card, I go to:

System -> Administration -> Hardware Drivers

And I've got the ATI accelerated graphics driver enabled

So is there anything I can do to make the graphics card to work correctly?

PS:Go easy on me, I'm new to linux, terminal commands etc, but willing to learn.   :)

Thank you very much

---

### Post by cyberdork33 on 2008-08-24
If you have desktop effects enabled, you can get odd effects with video and 3D graphics sometimes. Turn off desktop effects and everything works great.

---

### Post by goatchild on 2008-08-25
That didn't work. =/ 

I went to:

System -> Preferences -> Appearence -> Visual Effects -> None

Did I do somehting wrong?

---

### Post by cyberdork33 on 2008-08-25
> **goatchild said:**
> That didn't work. =/ 

I went to:

System -> Preferences -> Appearence -> Visual Effects -> None

Did I do somehting wrong?
what do you get from:
```
glxinfo |grep direct
```
and
```
fglrxinfo
```

---

