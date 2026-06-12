---
title: "Icons dont load in the desktop..."
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by jorgecarrillo150990 on 2007-08-30
I dont know what happened, suddenly all my icons dissaperared from the desktop, and also when I right-click the desktop, the menu doesnt appear.

Any help?

---

### Post by very_japi on 2007-08-30
It has happened to me before. You probably opened an unstable application (on my case it was eclipse). Did a simple reboot solve it?

---

### Post by jorgecarrillo150990 on 2007-08-30
> **very_japi said:**
> It has happened to me before. You probably opened an unstable application (on my case it was eclipse). Did a simple reboot solve it?
Yes but that has happened a lot, I reboot and still no icons appear, even if I dont have any applications open...

---

### Post by AlexenderReez on 2007-08-30
it something to do with nautilus......restart nautilus may help you.....

---

### Post by FuturePilot on 2007-08-30
Sounds like Nautilus crashed maybe.

---

### Post by jorgecarrillo150990 on 2007-08-30
how do I restart nautilus?

---

### Post by Pumm4 on 2007-08-30
> **jorgecarrillo150990 said:**
> how do I restart nautilus?
Open the Terminal (Console) and paste this:
```
nautilus -q
```This tells Nautilus to quit. Gnome will immediately restart Nautilus and new configuration changes will be loaded.

To open it:
```
gconf-edit
```

---

### Post by satbunny on 2007-08-31
I also suffer from this (Still on Edgy).

I tried

> nautilus -q

and the command line hangs.

I tried 

> gconf-edit


and I get > command not found

Could you perhaps explain in a different way?

---

### Post by Pumm4 on 2007-08-31
> **satbunny said:**
> 
Could you perhaps explain in a different way?
It seems that this (Nautilus thing) is not the problem ... I've just reacted to given solution and  tried to give more detail to it...

But never came across such situation > missing icons > no menu on right-clicking ...

Hope you find/get your answer soon ... [IMG]http://www.mysmiley.net/imgs/smile/winking/winking0050.gif[/IMG]

---

