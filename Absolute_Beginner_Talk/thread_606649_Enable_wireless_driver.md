---
title: "Enable wireless driver ??"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by celticbhoy on 2007-11-08
Just had to re-install Gutsy, and my wrieless card no longer picks up my network.

sudo lshw -C network shows the card is recognised but says it is disabled, so how do I enable the wireless card.

PS only internet access is through Vista.

---

### Post by zoom1 on 2007-11-08
I have the same problem with my card.. Product:BCM4318
any help?

---

### Post by celticbhoy on 2007-11-08
Got it with ndiswrapper.

Copy card's driver .inf file for XP to a directory of you home.
Install ndiswrapper using your Gutsy CD and synaptic.
cd to driver directory.

use :-

ndiswrapper -i <driver.inf filename>
ndiswrapper -m
ndiswrapper -mi
ndiswrapper -ma
sudo modprobe ndiswrapper

That worked for me anyway, hope it goes for you too.

---

