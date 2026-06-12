---
title: "Networking problems, probably hardware"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by p_quarles on 2007-05-29
Concise(-ish) backstory: my old Dell WinXP desktop has had problems with networking from the beginning. A couple months ago, the NIC stopped working completely. Previously, I had been able to use the modem to dial-up, reinstall the driver and get back up and running. The last time this happened, it wouldn't even recognize the modem. I was overdue for an upgrade, so bit the bullet and bought a new PC. Vista, consequently, forced me over to linux (and for that I, sorta, thank it).

A couple weeks ago, I realized that I had an extra computer (the Dell) that I could mess around with and break, in the interest of me learning how to do more things. I installed Ubuntu, bought a cheap Netgear ethernet card for it, and after a couple tries, got it to connect to my DSL modem and installed a couple packages. 

The next step was to setup a network. On the first try, the switch told me it was connected, but the Dell told me it wasn't. So, I took out the card, put it back in to make sure it was secure, and restarted, at which point it recognized the network connection. BUT: it wouldn't interact with the internet, as it had when I'd given it a direct connection to the modem. 

So, my gut feeling is that this is a hardware problem, probably with the PCI bus that connects the modem and the NIC to the motherboard--this would explain all the previous failures. At the same time, this is my first attempt to setup a home network in linux, and it's very possible that I'm just plain missing something. I read the official documentation, and as far as I can tell, the old PC is attempting to use IPv4. Advice is appreciated (but this is definitely not  urgent). 

Thanks.

---

### Post by jimrz on 2007-05-29
what type of network have you setup?
are you using a router to connect your 2 pc's and dsl? if not, would definitely recommend doing so + since you apparently do not need wifi you can get a nice name brand  4port + wlan router for dead cheap (think Comp or BestBuy had 1 for < $10 in their ad flyer this past weekend)

---

### Post by p_quarles on 2007-05-29
From my post above (emphasis added):

"On the first try, **the switch told me it was connected**, but the Dell told me it wasn't. So, I took out the card, put it back in to make sure it was secure, and restarted, at which point it recognized the network connection. BUT: it wouldn't interact with the internet, **as it had when I'd given it a direct connection to the modem**."

Yes, I am using an ethernet switch.

---

### Post by jimrz on 2007-05-29
> **p_quarles said:**
> From my post above (emphasis added):

"On the first try, **the switch told me it was connected**, but the Dell told me it wasn't. So, I took out the card, put it back in to make sure it was secure, and restarted, at which point it recognized the network connection. BUT: it wouldn't interact with the internet, **as it had when I'd given it a direct connection to the modem**."

Yes, I am using an ethernet switch.

yes, but what kind of switch. does it have a dedicated wlan port?
is it also a router? 
does it handle dhcp, dns, nat, etc? if not, check the settings on your comp, especially the dns ones since you seem to be having probs getting to the internet

---

### Post by p_quarles on 2007-05-29
D'oh. It says right on the box that the switch needs a router between it and the modem. That's what I get for thinking I'm smart. (sorry I yelled at you.) I'll go get one.

In the meantime, though, shouldn't the switch at least be able to connect my two PCs to one another? I'm not getting ANY interaction between the two, and neither identifies the other in Places/Network. Plus, I'm currently connected on my main PC through the switch. All of this is what leads me to think it's a problem with PCI bus on my older PC. Is my reasoning correct, or is this just all because I don't have a proper router?

---

### Post by jimrz on 2007-05-29
> **p_quarles said:**
> D'oh. It says right on the box that the switch needs a router between it and the modem. That's what I get for thinking I'm smart. (sorry I yelled at you.) I'll go get one.

In the meantime, though, shouldn't the switch at least be able to connect my two PCs to one another? I'm not getting ANY interaction between the two, and neither identifies the other in Places/Network. Plus, I'm currently connected on my main PC through the switch. All of this is what leads me to think it's a problem with PCI bus on my older PC. Is my reasoning correct, or is this just all because I don't have a proper router?

depends what you have setup and how configured. 

simplest would be a simple 4port + wlan router. i have had excellent luck with Netgear routers, both wired and wifi. they will, most of them, automatically setup with your dsl modem + provide dhcp + nat + other handy goodies. you will find that for networking (particularly samba, but also ssh) that identifying boxes by ip address rather than puter name works better. the router will (should) also allow you to "reserve" a specific ip for each box by puter name and MAC address, thus allowing you static ip functionality/certainty while still allowing the use of dhcp to keep network manager happy. i use all of the above and it works like a charm here.

once you get your hardware situated, you will need to install (a) samba [or nfs if all boxes are linux only] server on at least 1 box or (b) openssh server on both boxes or both, depending what you want to do. both server apps are available through synaptic, there are plenty of "how to" posts on these forums and, of course, plenty of people who can help with questions.

no need to apologize, no offense taken. but thank you for the thought.

---

### Post by p_quarles on 2007-05-29
Thank you very much for this information. It's starting to make sense now. In any case, I'm less concerned about connecting my old, buggy Dell than about connecting my soon-to-be-purchased laptop -- all of this helps very much.

---

### Post by jimrz on 2007-05-29
> **p_quarles said:**
> Thank you very much for this information. It's starting to make sense now. In any case, I'm less concerned about connecting my old, buggy Dell than about connecting my soon-to-be-purchased laptop -- all of this helps very much.

in that case, you probaly want to get a router with wifi capabilities. since you are not in a big hurry, watch the ads as these are "on sale" pretty regularly at various stores and on-line outlets. also, check out the wifi card/chipset before purchasing your laptop, as some wifi gear is much harder to get working with ubuntu/linux in general. if given a choice of cards go for intel then ralink then atheros chipsets, avoid broadcom and off the wall chipsets if at all possible. additionally, a little research on the laptops vid card can also avoid a lot of needless frustration.

---

### Post by p_quarles on 2007-06-02
Quick followup, because this is strange: one of my attempts at "fixing" the network config (before jimrz pointed out that a switch is NOT the same thing as a router--I still feel silly; for not reading the manual and stuff) completely killed Gnome. Since there was nothing on the drive, I reinstalled (Kubuntu this time). I wasn't expecting a working net connection, since my other computer was running . . .  but I accidentally discovered that it was fully connected. I was even able to browse the web and send e-mail on my primary system while the other one was downloading its updates.

This is more trivia than anything else, since I'm buying a wireless router, and I want to use the junker as a file server -- but how did this happen? Does the KDE network manager have built-in IP sharing? Is this a random accident?

---

