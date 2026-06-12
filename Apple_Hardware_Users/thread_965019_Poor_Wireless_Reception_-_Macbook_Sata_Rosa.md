---
title: "Poor Wireless Reception - Macbook Sata Rosa"
date: 2008-10-31
forum: Apple Hardware Users
---

### Post by hackntossh on 2008-10-31
I've experienced this issue with 8.04 and now with 8.10.  While wireless works fine the signal reception is much lower than if booted to OS X or Windows.  

8.10 shows 15% signal strength in an area I typically get 60 to 70% signal strength in OS X and Windows.  I would not mind the low signal but it constantly drops my connection.

Any ideas?

Cheers,
AP

Macbook Pro 3,1 Santa Rosa
2.2 GHz Intel Core 2 Duo
4G RAM
Ubuntu 8.10

---

### Post by clerik on 2008-12-08
I'm experiencing the same with XUbuntu. The best signal I had was 60%. Under Ubuntu, the device was recognized but it never connected on the network.

Under OSX Leopard, the sinal is always at 100%.


Mac Book Pro
2.33GHz Core 2 Duo
2G RAM

---

### Post by clerik on 2008-12-08
----

---

### Post by slikz21 on 2008-12-08
I'm having the exact same problem here. I was actually pleasantly surprised when wireless was working(somewhat) out of the box in the first place. 

Are there any more experienced users that would recommend different drivers than the standard ones?

---

### Post by Rog-Mahal on 2008-12-09
The ath9k drivers that are supplied with Ibex are the best bet you have. Madwifi had weak signal strength and is also not being supported anymore. I have not used ndiswrapper with the Atheros card in my Macbook, so that might be an option to explore, but it takes some work to get it up and running.

In my experience, this has been one of the tradeoffs that comes with using linux. I'm sure with updates signal strength will improve, but it will take some time.

---

### Post by shadowdude1794 on 2008-12-09
Out of curiosity, why would the software matter? Wouldn't the signal strength depend on the hardware?

---

### Post by cyberdork33 on 2008-12-11
> **shadowdude1794 said:**
> Out of curiosity, why would the software matter? Wouldn't the signal strength depend on the hardware?
The driver controls the hardware ;)

This is actually normal from my experience. Signal strength is always reported as being lower in Linux then in OS X (or windows).

---

### Post by SaiHayashi on 2009-03-07
> **shadowdude1794 said:**
> Out of curiosity, why would the software matter? Wouldn't the signal strength depend on the hardware?
put it this way,
a 60's CRT tv is no way capable of handling HD quality.
but a full HD LCD TV sure can display a really bad picture.

---

