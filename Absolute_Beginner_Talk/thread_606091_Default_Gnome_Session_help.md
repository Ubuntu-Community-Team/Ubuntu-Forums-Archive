---
title: "Default Gnome Session help"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by Evil Wayz on 2007-11-07
MY default gnome session has a graphical error, it alwasy goes to low graphics mode. I reconfigure, restart and boom, back to square one.

my failsafe however, works perfectly, the restricted driver and resolution are fine.  Which woudl lead me to believe that if i copy the contents of my .failsafe file to the default file, those settings would take effect.

Unfortunately I don't know what files i need to change.  If no one helps me, I'm going ot be forced to do what I always do, blow away the partition and reinstall.

And on that note, anyone have any idea how to back up your settings and installed packages?  I would like to have a way of restoring my os, as is when I screw things up.  Thanks in advance

---

### Post by Pumalite on 2007-11-07
Post your specs and tell me what iso you are using to install.

---

### Post by Evil Wayz on 2007-11-07
> **Pumalite said:**
> Post your specs and tell me what iso you are using to install.

not sure exactly what you meant but hopefulyl this is what you are lookign for:

using 32 bit 7.10

amd xp 3200+ cpu
1.5 gig rams
powercolor ati radeon 9800se

if you need the contents of certains files, let me know what ones you need and i'll hunt them down.

heres' whre the problem started:

i intsalled the newest ati driver with CCC. For some reason I removed and then reinstalled xgl. REad somewhere that new ati driverls were aixgl compatible and you should remove them. then i thought better of it. See what happens when you arm a fool with a little knowledge? 

I was browsing with swift weseal when my comp froze, and then rest. When i got to where the boot screen shoudl be, i got the message xserver cannont be displayed due to some error this display has been disabled. I was told to run dpkg-recongifigure for xerver and gdm. That is when i found that if i login to my default session it just returns me back to the login screen.  SO I was running gnome failsafe, which works perfectly. 

NOw my default session goes to low graphics mode, and aticonfigs says driver isn't enabled. but when i try to enable it and restart, i get the same cycle, low graphics, driver not enabled. 

Failsafe works jsut liek I want it to, but i dont think its wise to conduct all ym business on failsafe.

Let me know if that was what you are looking for.

---

### Post by Pumalite on 2007-11-07
I assume you have a system installed and you have only a problem with drivers. Well, the problem is ATI; it offers no support for Linux. Do a search of 'ATI Drivers and you'll see hundreds of posts  A lot of people complaining that if they enable Restricted Drivers, they have a messed up system. In any case, try ENVY and see if you have any luck. It would help me if you detailed the state of affairs in your system. Do you see Grub? Can you boot in Recovery Mode?.

---

### Post by Evil Wayz on 2007-11-07
> **Pumalite said:**
> I assume you have a system installed and you have only a problem with drivers. Well, the problem is ATI; it offers no support for Linux. Do a search of 'ATI Drivers and you'll see hundreds of posts  A lot of people complaining that if they enable Restricted Drivers, they have a messed up system. In any case, try ENVY and see if you have any luck. It would help me if you detailed the state of affairs in your system. Do you see Grub? Can you boot in Recovery Mode?.

Grub works, and so does recovery mode. And as long as i change session to gnome failsafe, everything works out great.  IT's only when i stry to start as default that i end up stuck in 800x600, using the vesa generic driver. What's envy and how do i use it?

---

### Post by Pumalite on 2007-11-07
ENVY is a script that installs your driver:[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Evil Wayz on 2007-11-07
I installed envy. Now i can't get TO my bootscreen its stuck at the upsplash.

---

