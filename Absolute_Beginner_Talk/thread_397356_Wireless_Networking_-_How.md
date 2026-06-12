---
title: "Wireless Networking - How?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by PaAk on 2007-03-30
Hello.
I installed Ubuntu today, and i got my first problem: I can´t get connected to my wireless router. The case is simple - i don´t know how i am supposed to do it.
Can someone help me?

Patrick

---

### Post by MEW on 2007-03-30
The first thing to find out is whether your wireless card has a driver installed (whether Ubuntu automatically detected it). Click System > Administration > Networking. Does a "Wireless connection" show up in the list of connections?

---

### Post by PaAk on 2007-03-30
It shows up the following 2 tabs:
Wired Connection
Modem Connection

---

### Post by morronix on 2007-03-30
Is this machine a laptop or a desktop? laptops normally have a option to switch off and on trough special keys (fn + F12,for example).After that,you verify again if the network card it's showed for you..

What's the manufacturer and the model of your network card?



I ask for you that forgives me for the bad english...

---

### Post by tbuss on 2007-03-30
> Hello.
I installed Ubuntu today, and i got my first problem: I can´t get connected to my wireless router. The case is simple - i don´t know how i am supposed to do it.
Can someone help me?

Patrick

Have you tried searching in the Networking & Wireless section? First you need to find out what chipset your card is using, there is a chance that it is supported by Linux. If so it could be as easy as installing the linux-restricted-modules. If you need more info on your card try lspci in the terminal. You can also try ndiswrapper, this will let you load a native windoze driver for your wifi card.  Wireless connectivity can be tricky, if you provide more info people will be more able to help.
> 
Is this machine a laptop or a desktop?

W> hat's the manufacturer and the model of your network card?

---

