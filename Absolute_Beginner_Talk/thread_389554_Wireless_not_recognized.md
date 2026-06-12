---
title: "Wireless not recognized"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by mdknaebel on 2007-03-20
I have a Farallon Skyline 11 mb pcmcia card (PN473) for my old world powerbook G3 running Xubuntu 6.10.

It doesnt work, it isnt recognized, but before, when I had Ubuntu 5.10, it did work.  My pcmcia does work, because I also have a working USB card

Any Ideas?

Thanks

---

### Post by crispy_420 on 2007-03-20
Does the OS load the driver? Or do you have the correct driver installed?

---

### Post by mdknaebel on 2007-03-21
It doesn't seem to do anything when I put the card in, the wireless card's light comes on but thats about it.  I haven't tried installing any drivers, I thought that Linux would do that for me...

Thanks

---

### Post by crispy_420 on 2007-03-21
Not all drivers are present by default. Do you know which one this card uses?

---

### Post by Death_Sargent on 2007-03-21
You may not want to hear this but i have had quite a few G3's have hardware burn outs (try a different pcmcia card any card) see if its not just a dead port

---

### Post by infol on 2007-03-21
try typing ```
lspcmcia
``` in a terminal when the card is plugged in to see if it is recognized by the system..

---

