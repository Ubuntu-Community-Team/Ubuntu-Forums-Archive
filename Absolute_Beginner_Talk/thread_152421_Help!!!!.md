---
title: "Help!!!!"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by belikralj on 2006-03-29
I have 2 problems:

1st:
Hi, I have 2 ethernet cards (internal PCI) I was wondering is there any way to set the default network settings from the command line and if so what file is it that I'm altering or should alter. by file I mean something like "fstab" is for auto matic mounting at startup and "menu.lst" is for boot loader options. Is there an equivelant for networking?

Usually it takes me 3 times opening system->administration->networking before my system accespts eth2 as default. I want to understand this better. ] (*,) 

2nd:
The "Add Applications" otpion has dissapeared from my Aplications menu. How do I restore it?   :-k 

Please and thank you   :D

---

### Post by ispmarin on 2006-03-29
There is a /etc/network/interfaces, where you can configure all the options to your ethernet card.

---

### Post by belikralj on 2006-04-16
I tried that but I wasn't sure of how to change it so I removed my other ethernet card and pluged in a router so it all works now. How ever I want to learn how to configure this computer properly by hand so if you could give me a link on how to change the /etc/network/interfaces I would really appreshiate it.

---

