---
title: "Philips Semiconductors SAA7134 (rev 01) - no picture"
date: 2005-11-06
forum: Absolute Beginner Talk
---

### Post by janne5011 on 2005-11-06
Hi all.I try to got this old card work...

Output of lspci is:
0000:00:0c.0 Multimedia controller: Philips Semiconductors SAA7134 (rev 01)
so far i done this:

Installed xawtv and vlc.
the status of this project is now I see nothing,no sign of life from the card.
what I shall do in vlc I dont know but I think its  best use xavtv first and get it to work there since I uses search and another guy was succesfull.
In xatv i use PAL:b/g
I followed instructions: 

lsmod | grep tuner
no output <----should be?
Question what best now to try?
thanks in advance:)

---

### Post by janne5011 on 2005-11-06
.. its solved only needed is to do this, I think  more people have this card:
first look here what card it is:
[http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)

then:

modprobe saa7134 card=YOUR# tuner=YOUR# oss=1
then put the same in etc/modules

---

