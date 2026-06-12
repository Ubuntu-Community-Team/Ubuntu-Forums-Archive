---
title: "Weird network problem."
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Brenlae on 2007-08-21
Well, here goes;
Everytime I log into my friend's PC I have to click once on the network connections icon (which says no connection established) and click once on Wired Network. Then I wait 10 seconds and bingo, no problem, connection established.

I'm just curious, is there anyway I could have this automated? It's a bit of a pain in the neck to have to do it every time he logs in, considering he's computer illiterate as well. :s

Anyway, any advice is thanked in advance. :)

---

### Post by Alterax on 2007-08-21
What it sounds like is that for some reason he is not getting the IP configuration through DHCP, although he should be getting that before logging on.  I get similar problems with my laptop's wireless connection (one of those Mac G4 jobs with the Broadcom card, for those that are curious, but that isn't really relevant.)

A quick fix would be to go to SYSTEM > PREFERENCES > SESSION > NEW.  Give it the name "Start up networking".  The command is gksudo /etc/init.d/networking restart

It's not the prettiest fix I can come up with on short notice; it is a workaround and will immediately prompt him for his password when he logs on.  But it should give him the network connection he needs until we get this figured out.

--Alterax

---

### Post by Brenlae on 2007-08-21
Thanks a bunch, I'll try that when I go over to his place tonight. :)

---

