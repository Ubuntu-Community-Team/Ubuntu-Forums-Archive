---
title: "I just upgraded to Feisty and I'm not getting Internet"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2007-04-30
Just like the topic title says, I just upgraded from Edgy to Feisty and the internet no longer works.  I really have no idea where to start diagnosing the problem.  Any help would be much appreciated.  

- Sheep

---

### Post by Cypher on 2007-04-30
Go to System->Administration->Network and ensure that you see a Wired Connection, ensure that it is either set to DHCP or has valid static information..

---

### Post by GrueTamer on 2007-04-30
A good thing to try if absolutely NOTHING works (note, this is a last resort option) is to get drivers for your network card off the internet or off of the cd that came with it if you have it and follow the install instructions for them.  This should work fairly well, and I in fact, once I find a good time to do it, have to go through the process on my older computer.  The install instructions (at least mine) look difficult, but aren't impossible.

Remember, don't try this until you've tried just about everything, I'm just posting this now so I don't forget :)

---

### Post by fatsheep on 2007-05-01
> **Cypher said:**
> Go to System->Administration->Network and ensure that you see a Wired Connection, ensure that it is either set to DHCP or has valid static information..

I have two wired connections, eth0 and eth1.  It doesn't matter if none of them are enabled, both are enabled, or one or the other is enabled - the results are the same: no internet.

---

### Post by tmatt95 on 2007-05-01
On my router at home, it will not connect to the Internet when Firefox has IPV6 switched on. To turn it off, load up Firefox and type in "about:config" in the address bar. Then, in the text box next to the word "filter" at the top of the screen, enter "ipv6". You will be left with one line saying, "network.dns.disableIPV6". Double click on it and the value should change to "true". When you restart Firefox, you hopefully will find that you can get online. 

Best Regards

Matt

P.S I have attached a screen shot of how it looks at the end of the process, with the value set to true.

---

### Post by fatsheep on 2007-05-02
> **tmatt95 said:**
> On my router at home, it will not connect to the Internet when Firefox has IPV6 switched on. To turn it off, load up Firefox and type in "about:config" in the address bar. Then, in the text box next to the word "filter" at the top of the screen, enter "ipv6". You will be left with one line saying, "network.dns.disableIPV6". Double click on it and the value should change to "true". When you restart Firefox, you hopefully will find that you can get online. 

Best Regards

Matt

P.S I have attached a screen shot of how it looks at the end of the process, with the value set to true.

Thanks you so much, that solved my problem instantly. :)

---

