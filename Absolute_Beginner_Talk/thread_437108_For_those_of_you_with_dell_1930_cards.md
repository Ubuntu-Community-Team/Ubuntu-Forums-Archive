---
title: "For those of you with dell 1930 cards"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Acglaphotis on 2007-05-08
This thread is for people with problems with the Dell Wireless 1390 WLAN Mini-PCI Card. I fixed mine with a simple command:

```
sudo aptitude install bcm43xx-fwcutter
```

It is that simple, when its installing it asks you if it can use some driver. Click yes, or ok or whatever it says. Then download wifi-radar ( sudo aptitude install wifi-radar ) and then your good to go. I dont know what harm can ndiswrapper do, but im sure i read somewhere that this broadcom card isnt supported but dont quote on this, since i **think** i read it.

I hope this clarifies some doubts.

-Acgla

EDIT: I think it only works on feisty.

---

### Post by jamiehd on 2007-05-08
I am going to try this now, but to be honest I will probably more pissed off if it does work than if it doesn't. I've spent hoursss trying to get my wireless working. :P

---

### Post by jamiehd on 2007-05-09
Thanks alot! It does work, nice one!

---

### Post by Acglaphotis on 2007-05-09
No problem!

-Acgla

---

