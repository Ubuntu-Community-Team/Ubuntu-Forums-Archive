---
title: "Internet connect is unpredictable and often doesnt work from boot. HELP!"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by (chubbstar) on 2007-04-15
I've been having trouble with my internet connection ever since i installed ubuntu a few months ago. At Seemingly random times, directly from reboot, my internet connection would stop working while just before rebooting is was detected and worked flawlessly. 

I've tried switching between static ip and automatic detection and both work, but again, randomly. Sometimes, when im really frustrated and dont want to use XP and i have time to kill, ill reboot incessantly until the internet is detected and this often works. But whats strange about this is i dont change any settings or do anything at all to fix the problem except merely rebooting. 

When eth0 is not detected all i am able to see is lo, loopback.

I use a D-Link WBR-2310 router and have cable internet.

---

### Post by kyphi on 2007-04-15
The first things I would look for is connectivity.

Check all your cables and connectors, are the lights on your router all working, front (and rear), is the light on for the connection to the computer.

An intermittent fault like the one you describe suggests a mechanical failure.

---

### Post by geezerone on 2007-04-15
Also, when you say you have no internet can you log into your router or ping it even?

---

### Post by (chubbstar) on 2007-04-15
yea, every time it hadnt worked the router was working fine for everyone and was connected properly and yet the internet would strangely only work in XP (consistently, ie it never DIDNT work)

and no i cannot ping the router, and when i go to ifconfig in the terminal i dont even have an assigned ip address. its just blank.

(coincidentally im in ubuntu now with the internet randomly working)

---

### Post by Seisen on 2007-04-15
What kind of NIC is it, that could be the part of the problem.

---

### Post by (chubbstar) on 2007-04-15
i dont know what NIC means. 

edit: ooooh. network card. it is an Intel PCI 82801DB PRO/100 VE (LOM) Ethernet according to the device manager. ie, a dell piece o crap.

---

### Post by Seisen on 2007-04-15
I figured out the problem, you network card isn't really supported, which would explain the problems with the connection. I'm trying to find a patch or something so I can help you fix it. I had the same problem with a D-Link Wireless card. The connection would go in and out all the time.

---

