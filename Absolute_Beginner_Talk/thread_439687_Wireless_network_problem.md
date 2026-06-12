---
title: "Wireless network problem"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by fr6zeros on 2007-05-10
I installed Wubi Ubuntu and still don't get internet connection, only Windows gets it.   I have an IBM laptop and my wireless adopter is 11a/b/g wireless LAN Mini PCI Adapter.  I think I have a driver problem.

---

### Post by AAM on 2007-05-11
I have WUBI on a win laptop and the wireless works just like normally - which is to say, it might be difficult to set up, but all the instructions are the normal ones. The only real difference seemed to be that WUBI set up eth1 for the wireless. 

Oh, yes .... AND ... also watch to see whether the wireless is actually turned on. You have to enter a long command starting with **cat** and ending with **rf_kill **or something like that. On my laptop the glowing button does not glow when switched on in linux.

---

### Post by ghostboy on 2007-05-11
> **AAM said:**
> I have WUBI on a win laptop and the wireless works just like normally - which is to say, it might be difficult to set up, but all the instructions are the normal ones. The only real difference seemed to be that WUBI set up eth1 for the wireless. 

Oh, yes .... AND ... also watch to see whether the wireless is actually turned on. You have to enter a long command starting with **cat** and ending with **rf_kill **or something like that. On my laptop the glowing button does not glow when switched on in linux.

AAM brings up a GREAT point.  I have an Acer Aspire 5050 laptop.  When I was running Windoze, the LED indicating I was connected to my network was always on, now the I am running Feisty, it doesnt come on.  Not a big deal for me.  

What kind of wireless card do you have?  These Forums of **FULL** of information on how to configure your wireless driver and workaround to get you on the net.

---

### Post by kame on 2007-05-11
Hey, I installed using Wubi (on a Dell Inspiron B130) and it automatically detected my wireless network. However, it runs horribly slow. Also, instead of having 'blue bars' (as what my friend has) to indicate signal strength I have two computers overlapping, and no way to see my signal strength. Does anyone else have a similiar problem?

---

