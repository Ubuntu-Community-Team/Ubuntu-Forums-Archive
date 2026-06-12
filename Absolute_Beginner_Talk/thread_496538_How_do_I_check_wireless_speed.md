---
title: "How do I check wireless speed?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by forsberg on 2007-07-09
I did the setup of my wireless driver (broadcom 4318) using the ndiswrapper method.

How do I check whether or not I am connecting at 54.0 mbps??

Network Manager just gives me signal strength, activity, and connection... nothing about the actual speed

---

### Post by AlexenderReez on 2007-07-09
type in terminal

> sudo iwconfig

---

### Post by djgrandmarquis on 2007-07-09
I've had a good experience with wifi-radar. It has a decent graphical interface. (You may need to disable Network Manger first, not sure.)

---

### Post by Papi-KB7VGW on 2007-07-09
GKrellM has a chart that shows what you are looking for.  Actually it will show  you almost everything going on in your machine.  Install it thru Synaptic.  :)

---

### Post by forsberg on 2007-07-09
Thanks guys.

The iwconfig command gives me the info I needed.

Will check out other GUI utilities for wireless.....

---

