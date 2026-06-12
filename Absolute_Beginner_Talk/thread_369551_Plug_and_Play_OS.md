---
title: "Plug and Play OS ??"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-02-24
Hiya

I've only just joined the forum today after I decided to install Ubuntu Edgy ( 1st timer) v6.10.

It's been a very pleasant learning curve so far and I have managed to get myself up and running with my DSL Router (DHCP) and install the following programs:

Xine
VLC
Crossover
Wine
Cedega

............. to name a few.  

I have never used Linux before today and was surprised at how easy it was to do this by following instructions and comments made by others on this forum.

Now I have come to a standstill and hope someone could advise me on this problem ?

Having installed KTorrent, I need to specify a MAC (physical) address for my NIC in my PC.  
This is required by my DSL Router in the NAT/DMZ Setup for Ports to be opened.

Within a Windoze/DOS  environment the command

ipconfig /all 

would suffice and provide me with this information.  I have checked the control panels as my starting point but cannot find any information regarding this.

Your help would be appreciated

chrome


BTW  

There was a 2nd question ..... (I'd forgotten already LOL ) .... is Ubuntu a Plug & Play OS ?? 

Now I have managed to get my PC up and running I was tempted to add my Technisat Skystar2 DVB-S (PC satellite card)

OR

my Philips SAA7134 Analogue TV card to the PC.

Are there any viewing applications that could be used for either device ??  Would Ubuntu pick them up and install the drivers for me ?

---

### Post by taurus on 2007-02-24
From a terminal, type

Applications -> Accessories -> Terminal
```
/sbin/ifconfig
```

---

### Post by annda on 2007-02-24
search synaptic for dvb and tv and see if any of the installable  tv viewing programs work for you and your cards.

some less-than-typical hardware can be tricky with linux as most manufacturers don't supply linux drivers and are hostile to the idea of publishing the specs of their products so that developers can create open source drivers.

so it's all trial and error for us users.

---

### Post by chrome307 on 2007-02-24
***@taurus***

Thank you for your quick reply and answer .. perfect :)
[B]
*@annda[/B]*

I will check Synaptic and do a 'Search' ............ Now why didn't think of that ?? :-D 

Finally will Ubuntu pick my hardware if I introduced them now ..... or should I have really have kept them in when I decide to take the plunge and install Ubuntu ??

Thanks again

chrome

---

