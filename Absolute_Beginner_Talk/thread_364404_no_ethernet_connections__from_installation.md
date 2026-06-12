---
title: "no ethernet connections ?? from installation"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by ihavenuthing on 2007-02-18
Is it possible that during the installation of ubuntu through the use of the live cd, some how destroyed my on board ethernet. 

List of events:
1) ran 6.10 live cd  ..... it ran just fine... I was able to test out the internet connection ( i.e. surf the net from the live cd )... then continued to install ubuntu...( kernel 2.6.17.10 )

2) after the reboot from installation... both linux and windows xp no longer are able to detect the on board ethernet....

3) ran the live cd again... but this time the internet doesnt work...

is there a solution to this problem? 

things i've tried....
1) ran lspci in linux ... but no ethernet cards found
2) tried to install the drivers in windows xp for the ethernet card but it says that the hardware could not be detected.....

thanks in advance

---

### Post by kinematic on 2007-02-18
if you ask me i'd say it's a freaky coincidence that your ethernet card died while you installed ubuntu.
it's not likely that ubuntu is the cause.

---

### Post by bulldog on 2007-02-18
Ubuntu shouldn't have anything to do with that,I think you have a bit of bad luck and your ethernet connection just died during the install.
I think so because windows can't detect it either anymore,so looking for an error is a waste of time.
But you can try to disconnect it from your modem/router and set everyting off,mode/router and the pc and disconnect it from the wall outlet.
Wait a few minutes and set everything on,and see if they are found again.

If this will not do anything good,you'll have to buy a PCI ethernet card,they cost a few bucks anyway,so this shouldn't set you off too much.

---

### Post by logos34 on 2007-02-18
You could try this (don't laugh): 
Shutdown the computer, turn off the power supply switch on the back of the pc and unplug the cord for 20 sec or so.  Plug it back in, flip the switch back, and boot up.  

I had a related problem dual-booting winxp and Suse 10.1: when I tried to use linux after 
windows I had to do above procedure to get an internet connection.  Although I could always detect the ethernet controller.  Maybe you fried it after all.

---

### Post by logos34 on 2007-02-18
Oh, I see Bulldog posted just before me.  So do what he suggested and just unplug everything.

---

### Post by ihavenuthing on 2007-02-18
OMG ahhaahha the miracles of a reboot hahaha thanks u guys

---

### Post by ihavenuthing on 2007-02-18
It works after the shut down :)  but when i reboot from the the OS the ethernet card is no longer detected.... has any1 have the same problem?

---

