---
title: "Ubuntu server acting as firewall"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by kgls13349 on 2007-02-20
Hey,
I have been thinking about replacing my horrid Belkin Router (with built in firewall) with a nice low power system running a linux firewall (Like smoothwall or something similar) but i am wondering if it is possible to setup a firewall app of some kind of my existing Ubuntu server so i only have one machine doing all the work,
My server is only a low power system (Via 1.5ghz C7) but from what i can tell pure firewall OS`s like smoothwall run on systems that are less that 100mhz so im guessing any software that might exist to do it with my ubuntu server shouldnt take much power.

My server is not used heavily, my home network only have two computer connected, one of which very rarely access the server at all, i do use it a bit, my muic and videos are stored on it, its just running a LAMP setup (although im yet to actually put a proper website on it) and Samba filesharing, oh and SSH so i can putty to it.

Any suggestions would be greatly appreciated, THanks!

---

### Post by dkohen on 2007-02-21
You shouldn't have any problem - I've been running my firewall/router on a Pentium II 350Mhz for years. I set it up with X but change the mode so that the firewall machine itself runs text-only. That let's me run Firestarter on X from my desktop and saves me from having to deal with the complexities of iptables. I like Firestarter because it is simple and clean, but covers most everyday needs. If you think about it, the processor in the Belkin is probably equivalent the a 386 - so for normal use almost anything that Ubuntu will install on should be adequate.

---

