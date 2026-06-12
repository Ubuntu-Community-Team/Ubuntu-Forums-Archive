---
title: "pleeeaseee help with gutsy!"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2008-02-10
Hi everyone


I just installed xubuntu 7.10 gutsy gibbon and I realized it did not recognized neither the wireless card nor the sound card.

I've also seen that a lot of people is having trouble with the sound in Gutsy, but I don't know if the solution works the same for everyone. And it is a little bit difficult to me to prove and ask my doubts because internet isn't working on Xubuntu....

So... what do I have to do to recover sound ???

Also internet would be wonderful if there is a way to configurate it easily and quick with Gutsy... because i remember for feisty or edgy you had to download some things and configure it manually... ( if I don't found anything I would end up searching for that but if there is an easier way now I would appreciate it a lot)

my computer is a HP Compaq nx6325, both devices are :

Broadcom Corporation Dell Wireless 1390 WLAN Mini-PC (wireless)

and I don't know which of this is my audio card but this is what I get:

SoundMAX HD Audio ( i think it is this one)

PremierSound audio/speaker subsystem
ADI1981HD High Definition CODEC
Integrated 16-bit Sound Blaster Pro compatible audio
24-bit DAC

---

### Post by spiderbatdad on 2008-02-10
do you have a working wired connection?

---

### Post by Jorge32 on 2008-02-10
> **spiderbatdad said:**
> do you have a working wired connection?

no, the only way is through wireless :S

---

### Post by spiderbatdad on 2008-02-10
try ```
sudo apt-get install linux-restricted-modules
``` hopefully the cd will be requested and you will be able to use the Restricted Drivers Manager to get your card working.

---

### Post by Jorge32 on 2008-02-11
ok i tried it and nothing... still the same

---

