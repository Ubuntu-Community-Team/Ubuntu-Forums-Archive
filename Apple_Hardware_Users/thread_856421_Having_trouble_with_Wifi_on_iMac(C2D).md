---
title: "Having trouble with Wifi on iMac(C2D)"
date: 2008-07-11
forum: Apple Hardware Users
---

### Post by vinny13 on 2008-07-11
Well I had followed a guide in which I cannot find right now on how to set up the Wifi on my iMac. Basically it ran ndiswrapper with a driver and my card could be detected. I connected to my network using something I cannot think of for some reason and I was up no problem. Then I think I attempted to give myself a Static IP but I'm pretty sure I filled in the wrong info and ever since then (everything erased and all) I cannot connect to web pages. Just web pages... In Mozilla I can connect to my router and I can download stuff off of Adept-Manager... I find that odd really, but I don't know much. I was surprised I installed everything on the right partition manually lol

Anyways, if someone can give me a solution for that, can someone also tell me how I can set ndiswrapper to start up as I log in because it's kind of annoying to go into terminal and launch it every time(sudo modprobe ndiswrapper I think?)...

I hope that all makes sense somewhat. Please ask if you don't understand something, I wanna get this fixed like today (away fro the next week) :)

---

### Post by damis648 on 2008-07-11
> **vinny13 said:**
> Well I had followed a guide in which I cannot find right now on how to set up the Wifi on my iMac. Basically it ran ndiswrapper with a driver and my card could be detected. I connected to my network using something I cannot think of for some reason and I was up no problem. Then I think I attempted to give myself a Static IP but I'm pretty sure I filled in the wrong info and ever since then (everything erased and all) I cannot connect to web pages. Just web pages... In Mozilla I can connect to my router and I can download stuff off of Adept-Manager... I find that odd really, but I don't know much. I was surprised I installed everything on the right partition manually lol

Anyways, if someone can give me a solution for that, can someone also tell me how I can set ndiswrapper to start up as I log in because it's kind of annoying to go into terminal and launch it every time(sudo modprobe ndiswrapper I think?)...

I hope that all makes sense somewhat. Please ask if you don't understand something, I wanna get this fixed like today (away fro the next week) :)

I do not know how to fix your webpage problem, but starting ndiswrapper on startup you can do the following int terminal:
```
gksudo gedit /etc/modules
```
gedit will appear with a small document. Simply add
```
ndiswrapper
```
as a new line at the bottom and save it.

---

