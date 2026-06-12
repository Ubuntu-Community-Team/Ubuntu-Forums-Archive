---
title: "MacBook Pro: battery life improvement with gutsy?"
date: 2007-07-16
forum: Apple Intel Users
---

### Post by [woodstock] on 2007-07-16
Hi!

I was wondering if anyone has already installed Gutsy on his/her MacBook Pro? I have read somewhere (I don't recall where) that one could expect the battery to last longer since kernel 2.6.21. As Gutsy comes with kernel 2.6.22-* there is some hope that the battery indeed will last longer. Can anyone confirm that or is battery life running linux still that much poorer than with OSX?

Woodstock

---

### Post by david_edmundson on 2007-07-18
Yes, the battery will be better in Gutsy than in Feisty. I don't know about you but I get much much better battery life in Feisty than in OS X, make sure your CPU is set to dynamic frequency and it easily outlasts OS X.

---

### Post by pveith on 2007-07-20
Longer battery life in Feisty as in OSX? Are you using a macbook C2D (non-pro)? If yes, did you do anything special to achieve the longer battery run?

Right now i have about 3,5 h battery-life on feisty and about 4,5 h on MacOSX (I installed sowftware and used a lot dvd-drive, so i could be even longer in OSX than that). Without doing much (just feq-scaling and low backlight).

(Arg just saw that this is about gutsy. Did you mean gutsy instead of Feisty in your first sentence? If yes, i think i will switch sooner than i thought...)

---

### Post by ronocdh on 2007-07-22
> **david_edmundson said:**
> Yes, the battery will be better in Gutsy than in Feisty. I don't know about you but I get much much better battery life in Feisty than in OS X, make sure your CPU is set to dynamic frequency and it easily outlasts OS X.
Please elaborate on your methods for maximizing battery life; I think it is a common theme in this forum that the battery life (admittedly in Feisty, not Gutsy) leaves a lot to be desired.

Also, if you're running the 22 kernel, try [PowerTop](http://www.linuxpowertop.org/).

---

### Post by pveith on 2007-07-23
Switched to gutsy which resulted in about the same battery-life as in feisty right now (this can and will probably change during development process). Will try powertop as soon as i have the time to find the "powersucking suspects".
Unfortunately the xserver-xorg-video-intel package no longer supports clone dual screen out of the box. So i will have to fiddle around again, but hey it is a development relase, it is not expected to be stable right now.

---

