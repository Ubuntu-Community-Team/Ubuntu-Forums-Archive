---
title: "Which version of ubuntu more compatible with my systems?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by sibot on 2007-06-26
I wanted to know which version of Ubuntu would be more compatible with my hardware:-

Processor - P4 3.0 Ghz HT
RAM - 1 GB DDR
HDD - 300 GB
GPU - Nvidia 6200 PCI-E
Sound - Creative Audigy Soundblaster 5.1
Mobo - DGGC101

thanks in advance,
Sibot

PS: I have tried Fiesty Fawn, but it gives me regular freeze ups.

---

### Post by vexorian on 2007-06-26
freeze ups could be a symptom of some bugged driver, I am not sure if you got some wireless LAN card in your system?

Your computer is much better than mine and mine runs Feisty Fawn + Compiz-fusion smoothly so you really got to check if there isn't a bugged driver outthere. Also check out your RAM memory, could have a failed chip.

---

### Post by mlentink on 2007-06-26
***All*** version should run. What is 'Mobo'? Your Wireless card?

Edit: I agree with Vexorian. Check wirelss and your ram

---

### Post by LaRoza on 2007-06-26
> **mlentink said:**
> ***All*** version should run. What is 'Mobo'? Your Wireless card?

Edit: I agree with Vexorian. Check wirelss and your ram


mobo = mother board

---

### Post by speaker219 on 2007-06-26
> **mlentink said:**
>  What is 'Mobo'? Your Wireless card?
lol, thats "Motherboard"

---

### Post by sibot on 2007-06-26
Thing is, if it was a memory problem, XP would've been giving me the problems too, but XP runs smoothly, I run it for days without reboot and it runs absolutely fine. While on the other hand, my Fiesty Fawn crashed every 10mins, but when i left it idle, it would go on for hours, as soon as i would get back on my computer, just surf the net or something, it would freeze up.

I donot have a wireless lan card in my system. Although I was getting error messages for that in my log. Which i later disabled but the problem still persisted. Mobo is motherboard. Mine being Intel DGGC101. 

Can HardDrive ever be a cause for the crash?

---

### Post by sibot on 2007-06-26
and..i did run a memtest for 2 - 3 hrs after which i got bugged, but everything uptill then everything went smooth. So i doubt if it could be a memory problem

---

### Post by mlentink on 2007-06-26
I agree. If XP runs fine on the same hardware, it's more likely than not to be a driver issue. But I don't know enough to tell you which, I'm sorry...

---

### Post by sibot on 2007-06-26
Its alright, thanks for replying!

---

### Post by sibot on 2007-06-26
Anyone? I plan upon installing ubuntu tonight. Any help would be much appreciated.

---

### Post by vexorian on 2007-06-26
> and..i did run a memtest for 2 - 3 hrs after which i got bugged

Could you elaborate?

...
Also, tried reproducing the freeze? could be an specific program? A good idea would be checking if live-cd also freezes eventually

---

### Post by sibot on 2007-06-26
Hmmm, yeah, well live-cd didnt freeze as far as i remember. But once when i was installing Fiesty, it froze during installation at "Installing Hardware". It runs for hours on idle, but hangs when I use it? Sounds fishy. Well, the memtest was taking too long and i lost my patience, as i wanted to get on Ubuntu asap, so i quit it.

---

### Post by miguel1986 on 2007-06-26
it freezes up? at which speed did you burn the livecd?

---

### Post by mlentink on 2007-06-26
> **sibot said:**
> It runs for hours on idle, but hangs when I use it? Sounds fishy. 'hangs when I use it' as in: when you use your keyboard, mouse and/or monitor?

---

### Post by sibot on 2007-06-26
To test out Ubuntu, I did a clean install, at around 12 am, I left the computer switched on for the night and went to sleep. Waking up the next morning, expecting ubuntu to have crashed, I was surprised to see it was still working. But after 10mins of working on it, it crashed. And was doing normal stuff, like surfin web, chattin on gaim et al.

---

### Post by mlentink on 2007-06-26
> **sibot said:**
> And was doing normal stuff, like surfin web, chattin on gaim et al.
Yeah, that's why I think it must be a driver issue. A driver that is not used when the machine is idle. But which one....

---

### Post by sibot on 2007-06-26
Hmm...its hard to pin point...i've been trying for the past month, posted a couple of times on launchpad, a million posts here. no relief uptill now.

---

### Post by sibot on 2007-06-27
anyone? any help?

---

### Post by vexorian on 2007-06-27
Hey how big of a swap partition do you use?

Also, I guess we can't do much besides telling you to find out which driver is causing the issues, list all of your hardware so we can find out if any of them got a driver that is known to have this problem,  if you got the will you can also try disabling each driver until no crash is experienced 

You may also try getting a widget like gnome panel's system monitor to find out processes that use too much CPU/memory so you get at least a suspect

---

