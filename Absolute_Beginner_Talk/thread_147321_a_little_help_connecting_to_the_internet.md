---
title: "a little help connecting to the internet"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by onewaytrip on 2006-03-20
ok my problem is getting my linksys wireless network adapter to work with ubuntu.first let me just say i search the forum already for this topic and found lot of post about it but i just dont seem to understand how everything works yet. second the only way i can access the internet is with my network adapter i dont have my own isp so i just jump on nearby signals. now when i go to the device manager the adapter shows up but has a few unknowns. so can any of ya help? i really want to start working on ubuntu but without the internet im at a block in the road.

---

### Post by Brunellus on 2006-03-20
you need to figure out what network you want to connect to.  in network management, you'll see the name of your wlan adaptor--probably something like wlan0 or ath0.

then open a terminal and execute

iwlist wlan0 scanning

That'll list all access poitns in the area.  find one essid that looks promising, and put that name into the "wireless" connection bit. 

I'm on dapper now, and there's evena  GUI for this in the network setup.  But don't know/remember how breezy works wrt to it.

---

### Post by onewaytrip on 2006-03-20
so i need to type iwlist wlan0 scanning in the terminal and it will list all avalible access point ok seem simple enough but what about all that talk about ndiswrapper i been reading everywhere? well i give your suggestion a try but i have a feeling thats thats only for dapper and i might need to do more for breezy. thanks ill post my result when im done.

---

### Post by Sendervictorius on 2006-03-20
[QUOTE=onewaytrip]so i need to type iwlist wlan0 scanning in the terminal and it will list all avalible access point ok seem simple enough but what about all that talk about ndiswrapper i been reading everywhere? well i give your suggestion a try but i have a feeling thats thats only for dapper and i might need to do more for breezy. thanks ill post my result when im done.[/QUOTE]


You may be lucy, and it works out of the box. If your wireless card is not supported you will need to do the ndiswrapper thing.:cry:

---

### Post by Papa-san on 2006-03-20
Not all of them support scanning, though. Hopefully yours does, 'cause mine doesn't... This is one of the reasons I am still stuck..

---

### Post by Brunellus on 2006-03-20
[QUOTE=onewaytrip]so i need to type iwlist wlan0 scanning in the terminal and it will list all avalible access point ok seem simple enough but what about all that talk about ndiswrapper i been reading everywhere? well i give your suggestion a try but i have a feeling thats thats only for dapper and i might need to do more for breezy. thanks ill post my result when im done.[/QUOTE]
the large volume of ndiswrapper threads (and to a lesser extent, threads about other wireless drivers--RT2400/2500/2570 and so forth) is due to the fact that support for those chipsets is not as good as for others (prism2, prism54, atheros).  So what you'er seeing is the online equiv of the squeaky wheel being greased.

It's entirely possible your wlan card was supported out of the box (do a happy dance.  NOW!), so all you have to worry about is finding an AP to connect to.  Again, not sure how it was in breezy (I only ever connected to one AP) but there might even be a pulldown menu for this in the 'properties' of the wireless card in the "networking setup" GUI.

---

### Post by onewaytrip on 2006-03-20
i think i might have to try thata ndiswrapper thing cause i tried the suggestion mention earlier in this thread but it didnt work and it said scanning not supported so any other suggestion please. also thanks for the info so far.

---

### Post by Brunellus on 2006-03-20
ndiswrapper is a wrapper for windows wireless device drivers.  It is only really necessary if your card is not supported natively.

As your card is supported natively, you're in a (relatively) lucky spot.

What didn't work?

Please provide as accurate a report of what you did (commands and especially OUTPUT).

---

### Post by onewaytrip on 2006-03-20
ok i try what you said to do earlier Brunellus but nothing work in the terminal it kept saying that interface does not support scanning when i type in wlan0 or ath0 and thats all that happen. also i look all over the ubuntu os for the network management and didnt find anything that said network management.
anymore ideas? im completely loss on this one, it hard switching back and fourth from ubuntu to windows.

---

