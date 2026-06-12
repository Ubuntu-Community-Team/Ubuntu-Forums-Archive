---
title: "Wifi connect on startup"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by rogerdean on 2006-02-03
Just a quickie folks...
I'd like one of my Wifi cards to connect to the network automatically when I boot up (breezy, don't mind whether it's the laptop's internal card or the pcmcia). As it is both cards work fine but I have to go to system-admin-networking and 'activate' them. Is there a way round this?
Cheers
Roger

---

### Post by moephan on 2006-02-03
FWIW, my wireless card connects at startup, I think because it is set as the default gateway device in the network admin tool.

---

### Post by bscbrit on 2006-02-03
In /etc/network/interfaces make sure that one of your cards is set up as

auto wlan0 (or whatever your card is known as)

---

### Post by rogerdean on 2006-02-03
many thanks folks :D

---

