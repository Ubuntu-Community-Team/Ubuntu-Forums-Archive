---
title: "Wireless Internet Connection"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by jasrog on 2007-02-12
I have a toshiba laptop with Ubuntu 6.10 installed and can connect to the internet with ethernet connection to cable modem, but when I try to connect wireless I cannot get online. I have atheros wireless network and are trying to connect via linksys wireless router...Help Please.

---

### Post by crispy_420 on 2007-02-12
First of all, does ubuntu see your wireless card?

System -> Administration -> Networking

So laptops require that you "turn on" your wireless card, in my case Alt + F2. That had me screwed up for a bit of time. This is not a bad thing, just turn off your connection when you don't need it.

Test your network with all security off, and then work up from there.

It is not your chipset, I have the same chipset and it worked right away.

Also as a side note, look into network-manager. It will simplify your life.

---

### Post by jasrog on 2007-02-16
No going to system administration networking reveals only wired connection...no wireless one.

---

### Post by crispy_420 on 2007-02-17
Have you installed the restricted modules for your kernel?

That is where the atheros (madwifi) drivers are.

Use symantic and search "atheros".

---

