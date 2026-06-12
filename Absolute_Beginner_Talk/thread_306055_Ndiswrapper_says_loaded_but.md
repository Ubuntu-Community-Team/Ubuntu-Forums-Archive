---
title: "Ndiswrapper says loaded but"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by Recked on 2006-11-24
Hello,

I have asked this in another thread but thought perhaps I might have better luck in beginner thread.

I have installed ndiswrapper and the XP driver for my Netgear WPN511 cardbus nic card and it works, but each time I shut my laptop down or reboot and I have uninstall the driver and then reinstall it for the nic card to work again.

Does anybody know where I need to make a manual change so the driver is loaded automatically each time the machine comes up?

Thank you

---

### Post by az on 2006-11-24
sudo gedit /etc/modules

and add the word

ndiswrapper

to the end of the list.

---

### Post by Recked on 2006-11-24
Thanks much Azz. 

I will give this a whirl when I get home

---

