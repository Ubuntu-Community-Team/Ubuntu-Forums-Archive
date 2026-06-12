---
title: "Internet connection sharing with an XP box"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by rubrboots on 2006-04-07
Hello all

I am trying to get my ubuntu box on line via a crossover cable to my xp box. The xp box is connected to the internet via a wifi card to a router in the basement.

Before I waste anymore time I want to make sure this is even possible? Or worth the time?

Thanks:)

---

### Post by OfficeLinebacker on 2006-04-07
[quote=rubrboots]Hello all
 
I am trying to get my ubuntu box on line via a crossover cable to my xp box. The xp box is connected to the internet via a wifi card to a router in the basement.
 
Before I waste anymore time I want to make sure this is even possible? Or worth the time?
 
Thanks:)[/quote]
 
I've had Ubuntu clients hooked up to the internet via XP boxes' ICS facility before.

---

### Post by rubrboots on 2006-04-07
Ok this is what I have set up.

I have the wireless connect ICS turned on the XP wifi connection, and I have a static IP set on the NIC on the XP box. I also assigned a static IP in ubuntu.

I think I set up the NIC properly in Ubuntu, is says that it is ACTIVE. I can ping the ubuntu box, but I cannot ping the other computers on the network even though the xp box still has an internet connection. I know this sounds like a mess, but I am not that great at networking, and I know nothing about linux yet.:-k

---

### Post by eriefisher on 2006-04-07
I would try disableing the XP firewall for the NIC connecting to the ubuntu box. You can right click on that connection, goto properties I think and it should be in the advance settings.

eriefisher

---

### Post by rubrboots on 2006-04-07
Ok I turned off my norton firewall, and confirmed that the XP firewall is OFF. But still not internet on the Ubuntu.:confused:

---

### Post by rubrboots on 2006-04-07
I just remembered that there is MAC address filtering on my router. Can anyone tell me how to find the MAC address in Ubuntu.

---

### Post by eriefisher on 2006-04-07
You are using a router and XP firewall and Norton? That's pretty excessive. The first thing I would do is get rid of that Norton stuff.

In Ubuntu I think if you open a terminal and type ifconfig you should get the info you need.

eriefisher

---

### Post by rubrboots on 2006-04-07
LOL, No I am using a router and Norton firewall, XP firewall is always disabled. I have heard that a router acts as a firewall but I dont really understand how that works, so I leave it as is.

---

### Post by rubrboots on 2006-04-08
Ok now I have added the MAC address of the Ubuntu box, but still no Internet connection.](*,)

---

### Post by gam3r on 2006-04-09
I got the same setup/problem..Me is a new user to ubuntu as well :)

---

