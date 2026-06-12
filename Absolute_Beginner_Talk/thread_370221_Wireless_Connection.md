---
title: "Wireless Connection"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by brontosaurus on 2007-02-25
I have an Apple iBook G4, and I recently installed Ubuntu on a partition.  One of my friends got the Broadcom drivers working for my Airport card, but I've been having problems with my wireless connection.

Whenever I boot in Ubuntu or get out of "Suspend" mode, my internet stops working.  My wireless connection has an ascii encoding, so I've been going into the networking utility, changing the settings to hex, then changing it back, and then the internet works.  This is obviously very annoying, so I'm wondering how I can make it work from the getgo.  Thanks!

---

### Post by solar george on 2007-02-25
Open the terminal and type,

```
sudo ifdown wlan0
sudo ifup wlan0
```

Where wlan0 is the name given to you wireless card.

---

### Post by brontosaurus on 2007-02-25
Thanks.  Any clue why this is happening?

---

### Post by Armor on 2007-02-25
For whatever reason, it seems as if your network card isn't being initialized after shutting down? Just a guess

---

### Post by solar george on 2007-02-25
Wireless cards aren't always reconnected after suspending and occasionally during bootup if the signal is weak. I don't know why, it just happens.

---

