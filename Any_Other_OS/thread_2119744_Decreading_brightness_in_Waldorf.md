---
title: "Decreading brightness in Waldorf"
date: 2013-02-24
forum: Any Other OS
---

### Post by kabukiM0n0 on 2013-02-24
Hey there guys!! 


I've been desperately trying to lower my screen brightness for a few days now, as it's slowly burning my eyes out and I cannot seem to find a way to do so. 

The brightness fn keys do not respond, they actually don't respond on any distro apart from Ubuntu. 

I've tried xbacklight but it responds "no outputs have backlight property" 
so I did a search and see what I could find. 
Apparently it is a driver issue. But the posts are in the Arch forums and am not sure if that's applicable to debian.
But as I'm pretty green with debian, there are certain things I still just don't understand how to do - and most of what's said in them posts is way above my knowledge. Anyway. 

Does anyone know of a way to be able to turn down the brightness, as it's starting to feel as if I'm staring directly into the sun.

EDIT: I've found a temporary solution. 
sudo setpci -s 00:02.0 F4.b=XX. 
The XX is the level of brightness; 0 being the darkest, 100 brightest
For anyone having similar problems. Even though it's temporary and has to be introduced every time the system is booted I'll mark this as solved. I have no issue constantly typing this simple command in!!!!

---

### Post by kabukiM0n0 on 2013-02-24
Just adding a clean post on how to, so it's clear to anyone with the same issue - as it's taken me quite some time to figure this out. 


```
sudo setpci -s "00:02.0" F4.B=XX
```The XX is the level of brightness; 0 being the darkest, 100 brightest

The same command can also be added into ```
sudo gedit /etc/rc.local
``` above ```
"exit=0"
``` that way, the system will start-up with a specific brightness.

---

