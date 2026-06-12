---
title: "Wlan card shows available net but doesn't connect"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Caldi on 2007-05-03
Hi everyone,

I recently decided to give Linux a try and yesterday set up Ubuntu on my old laptop. Up until now, nearly everything works out of the box except my WLAN card which gives me some trouble (and my USB mouse which I can't get to function :confused: )

I managed to install the drivers for my WLAN PCMCIA card (FibreLine WL260X, based on a Realtek 8180L) to show up and get the drivers running by using ndiswrapper and the drivers form my Windows XP installation. The card seemed to work, it showed my the available networks (mine and the one from my neighbor too...), I choose my network, punched in my WEP key and unplugged the annoying LAN cable from my laptop - but the card somehow does not connect to the network, and yes, I already double( triple actually)checked the WEP key, even tried it in HEX or ASCII, nothing did work. Now I am kinda lost... I have net acces over LAN and so I can atleast look for help here :)

---

### Post by mikeyphi on 2007-05-03
Had a similar problem with a different card - had to change the Router to 'Open' broadcast before it would connect my card.

---

### Post by Famicommie on 2007-05-03
First of all, HEX key is the way to go. I almost never have success trying to use ASCII or the WEP password.

A problem that I had was that my neighbor and I were both using the same channel on our routers. I am not sure what the technical details are, but my card began to work flawlessly as soon as I switched the channel on the router.

---

