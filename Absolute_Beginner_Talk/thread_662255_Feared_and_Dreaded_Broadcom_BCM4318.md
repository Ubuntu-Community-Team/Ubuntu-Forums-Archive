---
title: "Feared and Dreaded Broadcom BCM4318"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Tatsu08 on 2008-01-08
Forgive me for making a thread about a subject that's been stated numerous times, but I've been browsing, mimicking, downloading, more mimicking, more browsing ... and I've been to more tutorials than I thought existed for anything.  I can work around Windows pretty well, but Ubuntu/Linux is confusing me right now.

Today, I installed Ubuntu 7.4 from a CD my friend gave me.  I then updated to 7.10 Gutsy.  This was roughly 2pm.  It's 8pm now.  I've been trying to get my wireless card to work for nearly 6 hours straight, and still nothing.

ndiswrapper is confusing to start.  It says it's installed, then I do the ndiswrapper -l to verify, and it says it's not installed.  It then says, to install, type a command pertaining to ndiswrapper-common, and it loops me around like those 'how do you keep an idiot busy, look on the other side' gigs.

I've also seen and tried a few 'install your evil broadcast wireless card without ndiswrapper' tutorials, but those have failed too.

My computer is a Compaq Presario V2000, AMD64 Turion (single core, old school style) with the aforementioned integrated wireless card:  Broadcom BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02).  Bluetooth included.

I'd love to continue using Ubuntu, it seems nicer than Windows thus far, but if I can't get wireless to work before classes start on Thursday, I'm going to have to revert back.

---

### Post by stump138 on 2008-01-08
I was never able to get the bcm4318 to work in a laptop until I did a fresh install of 7.10 from the alt cd.

I have tried in last 4 ubuntu releases with no luck.  I don't think there isn't a how-to I tried.  Best I can say is good luck, but I honestly think that getting the broadcom to work is practically pure luck.

---

### Post by stump138 on 2008-01-08
one thing you can try is enabling the broadcom firmware in the restricted drivers manager if you haven't already

---

### Post by exactopposite on 2008-01-08
in gutsy the rescrited drivers manager took care of what i needed for my bcm43xx.  i just needed to hook it up to an ethernet connection to downoad the driver.

---

### Post by Tatsu08 on 2008-01-08
> **exactopposite said:**
> in gutsy the rescrited drivers manager took care of what i needed for my bcm43xx.  i just needed to hook it up to an ethernet connection to downoad the driver.

could you elaborate a little more on this please?


and stump, I tried that, and nothing seemed to change :-\

---

### Post by undertakingyou on 2008-01-08
Go to SYSTEM => ADMINISTRATION => RESTRICTED DRIVERS MANAGER
From there you should just need to check a box, have it download what it needs, and then restart.

---

