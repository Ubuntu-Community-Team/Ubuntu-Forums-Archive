---
title: "Cannot connect to internet, yet connection was fine yesterday. ;?_?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by ARandomKid on 2007-09-09
Xubuntu 7.04 wouldn't connect to the internet and so I posted a different topic about that.

One poster (forget the name) gave me the wonderful idea of setting the static ip to my router's settings. (Didn't explicitly say this, but I tried it anyhow) It worked.

However, I accidentally close the monitor, shutting my computer off. I boot it back up and the internet refuses to connect even though I've unplugged and replugged in the ethernet modem, and done /etc/init.d/networking restart like always.

I've even waited 12 hours. ;@_@

---

### Post by sumguy231 on 2007-09-09
Look at /etc/network/interfaces and see if the information for eth0 is correct.

---

### Post by ts51 on 2007-09-09
Do what sumguy 231 said.....


That's the only logical thing to do without re installing

---

### Post by ARandomKid on 2007-09-09
It should be correct, as I haven't messed with it at all.

I'll verify it, though.

---

### Post by ARandomKid on 2007-09-09
OK, now I get SIOCADDRT: Network is unreachable.

---

### Post by cmnorton on 2007-09-09
If you have a router set up with the ethernet modem (cable? dsl?), recycle the power on that as well. For your ethernet modem, did you only recycle the power or did you also press the reset?
Is this the only computer that cannot connect?

I am asking these questions because:

1) I have to recycle either my wireless router, dsl modem, or both, and I had to do this extensively while testing tunneling with pptpconfig. 

2) If you have a router set up with your ethernet modem, and somehow the router's reset button was pressed, then you would have to establish "pass-through" in the ethernet modem, so that it is not acting like a mini-router. (My DSL modem has router/dhcp capability, which is disabled in favor of the linksys router/firewall.)

---

### Post by ARandomKid on 2007-09-09
> **cmnorton said:**
> If you have a router set up with the ethernet modem (cable? dsl?), recycle the power on that as well. For your ethernet modem, did you only recycle the power or did you also press the reset?

Heck, I just unplugged it. It doesn't really have a reset feature. Unless you count the whole networking restart thing as resetting this.

> **cmnorton said:**
> 
Is this the only computer that cannot connect?

Yes.


> **cmnorton said:**
> 2) If you have a router set up with your ethernet modem, and somehow the router's reset button was pressed, then you would have to establish "pass-through" in the ethernet modem, so that it is not acting like a mini-router. (My DSL modem has router/dhcp capability, which is disabled in favor of the linksys router/firewall.)

You just gave me another wonderful idea...

EIDT: Which didn't work. As usual. ;>.> I figured that maybe if I reset the router and modem as well as the ethernet card, it might work...

---

### Post by mendingo84 on 2007-09-09
if you can connect to Gaim than you connection works fine and the problem is with one Firefox setting

---

### Post by ARandomKid on 2007-09-09
I can't connect, but this is probably because I don't have an IM account to begin with.

---

### Post by owlboxman on 2007-10-15
I know this thread is now a bit old, but it sounds similar to a couple of occasions I have experienced. Both the router and my Ubuntu desktop showed the ethernet connection as working, and my Windows desktop connected fine wirelessly, but both Firefox and Evolution simply refused to connect. In both cases it happened after a power cut, once when the computer was working  and once when it was shut down. I suspect the correlation with the power cuts is not just coincidence. In both cases I booted from the live CD, and Firefox connected without problem. I shut down and then booted normally and found the internet connection was working fine again.

---

