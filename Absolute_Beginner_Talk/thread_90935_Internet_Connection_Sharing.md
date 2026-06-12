---
title: "Internet Connection Sharing"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by ubuntufella on 2005-11-16
Hi. I am running a dual boot situation with windows and I do ICS on it without a problem. I was wondering what I have to do on Ubuntu so I can share the connection and maybe files and the printer between my Windows laptop. I have already set eth1 to 192.168.2.1 with the appropriate subnet mask, and set the laptop to 192.168.2.2 with the appropriate subnet mask. The laptop say it has connected fine (none of this limited connectivity business)so where do i go from here? Any help greatly appreciated.

---

### Post by matthewv on 2005-11-16
[QUOTE=ubuntufella]Hi. I am running a dual boot situation with windows and I do ICS on it without a problem. I was wondering what I have to do on Ubuntu so I can share the connection and maybe files and the printer between my Windows laptop. I have already set eth1 to 192.168.2.1 with the appropriate subnet mask, and set the laptop to 192.168.2.2 with the appropriate subnet mask. The laptop say it has connected fine (none of this limited connectivity business)so where do i go from here? Any help greatly appreciated.[/QUOTE]
If ICS is enabled on your win xp machine, its IP address will be 192.168.0.1 . Set your gateway to that address, and fill in the primary and secondary dns servers from your isp. ICS should then work. Files can be shared too, try Places --> Network Servers. For a printer, go to System --> Administration --> Printing. Select  new printer, and select a nework printer --> Windows Printer (SMB). Fill in the appropriate info, click next, select printer model and you should be set.

---

### Post by ubuntufella on 2005-11-16
I don't think I was clear on what I have done. :p I have Windows installed on this computer as well as Ubuntu. Just saying it worked fine in XP. Sorry :p

---

### Post by Stormspace on 2005-11-16
If you have a broadband connection, I'd suggest buying a 59.00 router from Walmart and use it. You may even be able to pick up a wireless B router from someone wanting to upgrade to G. 

If you are on dial-up however I can't help you, however I do have an old LAN modem that works great. It does however, keep the connection open all the time. 3com made this one and may make them still, but I don't know how much they are as I inherited this one from a buddy. :)

---

### Post by ubuntufella on 2005-11-16
Well, I connect to the internet through a router already that has everyone in my house on it. What I am trying simply though to do (router is several metres away from my room) is to share my connection to the router using 2 NICs and a crossover cable.

This is so that I can share the connection from within my room, which I can already achieve using the XP Connection sharing business.

But I wouldn't mind knowing how to do it on a software basis. I am to understand that itables has the ability to do this, but from what I hear, it can be done using the network seup wizard.

Thanks

---

### Post by Stormspace on 2005-11-16
[QUOTE=ubuntufella]Well, I connect to the internet through a router already that has everyone in my house on it. What I am trying simply though to do (router is several metres away from my room) is to share my connection to the router using 2 NICs and a crossover cable.

This is so that I can share the connection from within my room, which I can already achieve using the XP Connection sharing business.

But I wouldn't mind knowing how to do it on a software basis. I am to understand that itables has the ability to do this, but from what I hear, it can be done using the network seup wizard.

Thanks[/QUOTE]

That is just so wacked. :) So you are basically using the PC as an inline coupler to put two wires together? Dude, get a 10.00 switch or hub and put it in the room and plug the router and PC's into it. The only reason to do what you are doing is if you want to somehow run a firewall to keep all the other PC's in the house off your box.

---

### Post by ubuntufella on 2005-11-16
Not really. Why buy a $10 router or hub when I can use a NIC that I already have? It's not like you can't do it, I can and do when I run Windows, and I want to be able to when I run Ubuntu. I could buy a router, but why? Do you want a network diagram? I know it can be done, and I don't plan to orget doing it. I don't want to block other PCs in my house off my machine, it is just very convenient to do it this way. Thanks again.

---

### Post by onesojourner on 2005-11-16
Internet connection sharing can be usefull. at one point I put a wirless card in my desktop along with a nic. then shared the wireless signal out to another wirless router. I would like to know if it can be done with ubuntu.

---

### Post by Stormspace on 2005-11-16
[QUOTE=ubuntufella]Not really. Why buy a $10 router or hub when I can use a NIC that I already have? It's not like you can't do it, I can and do when I run Windows, and I want to be able to when I run Ubuntu. I could buy a router, but why? Do you want a network diagram? I know it can be done, and I don't plan to orget doing it. I don't want to block other PCs in my house off my machine, it is just very convenient to do it this way. Thanks again.[/QUOTE]

Using a PC as a hub is just inefficient and creates a drain on the machine sharing the connection, not to mention now all the other boxes connected to it rely on that PC being on. For me a 10.00 expense for a hub and 2 minutes worth of work hooking it up is preferable. But have at it, it's certainly a skill that could be useful if you ever find yourself without a router. :)

---

### Post by kruz on 2005-11-16
that much info on the nic
which is prolly onboard?
which is prolly eating at least 50% of ur adress bus while its connecting

it doesnt go strait from nic to nic
it goes
nic to adress bus to cpu to os, back to other nic and out
same with in , in reverse

very inefficient

also

sudo apt-get install samba

save yourself some time and buy a router

and ull notice a huge speed increase

well not huge, but both pc's will in fact run faster

---

### Post by ubuntufella on 2005-11-17
Ok. It's obvious that I am going to find no help here.

---

### Post by matthewv on 2005-11-17
[QUOTE=ubuntufella]Ok. It's obvious that I am going to find no help here.[/QUOTE]
Before you give up totally, I was just looking at firestarter, which is installable from the repos. Apparantly, and I haven't tested it, it can share out a net connection and function as a dhcp server. You might want to give it a try. Just follow the instructions on their site.

---

### Post by ubuntufella on 2005-11-17
[QUOTE=matthewv]Before you give up totally, I was just looking at firestarter, which is installable from the repos. Apparantly, and I haven't tested it, it can share out a net connection and function as a dhcp server. You might want to give it a try. Just follow the instructions on their site.[/QUOTE]
I installed it but opted out for the dhcp server, and now it works a treat. Thanks a lot for your help man!

---

### Post by Stormspace on 2005-11-17
Good luck. I hope you get it going. It's also a good way to connect a second machine to monitored network where only one IP per person is allowed. Like in a dorm room. :)

---

### Post by rooster on 2005-11-17
Edited

I should have read to the end next time.... Sorry!

---

### Post by ubuntufella on 2005-11-19
[QUOTE=rooster]Edited

I should have read to the end next time.... Sorry![/QUOTE]
Don't mention it!

---

