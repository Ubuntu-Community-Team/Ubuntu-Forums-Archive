---
title: "Getting IPv6 going"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by nazzer on 2007-04-25
Hi all

I'm very new to ubuntu (installed it yesterday) and expected the IPv6 stuff to be going first up. 

On checking it isn't - can someone give me some guidance please? it doesn't need a tunnel as my home f/w terminates a tunnel to the IPv6 world. All I want are the drivers to go and the f/w uses radvd to allocated addresses.

I'm not new to unix - just veeeeery rusty. :-)

Yes, I see some other commentary around the place complaining about slowness and timeouts, that shouldn't be a problem for me as I have a working IPv6 LAN I am connecting to.

TIA


Nazzer

---

### Post by russell.h on 2007-04-25
My understanding was thatt IPv6 is enabled by default (it was on my Feisty, not sure about Edgy). Lots of people are looking to turn it off for that reason, which is why you've probably seen it mentioned.

What version of Ubuntu are you running?

---

### Post by nazzer on 2007-04-27
No, neither  edgy (yesterday's version) nor feisty (today's) have IPv6 enabled... it seems to be 7.04, was 6.8... how embarrassing all the M$ machines on my LAN can do v6 but not the new linux lappie. LOL

I can't see in /etc/networks where this should be set up... what drivers should be where to do IPv6? What is needed to get it to request an address?

Naz

---

### Post by Najand on 2007-04-27
Mine has it working, check it using ```
ip a | grep inet6
```

---

### Post by nazzer on 2007-04-28
Aah thank you, "ip a" tells me what's running and what isn't. Turns out it was - I was getting an fe80 address, but no global address.

Restarted my tunnel broker (which runs on my firewall, not this machine) and yes, now I have a global address... sounds good...

ping6 [www.kame.net](www.kame.net)  - all good 
point browser at v6 enabled sites, and NO DANCING TURTLE!!! Que???

Kills browser, restarts, still no dancing turtle... why doesn't the browser use ipv6?? That's just *wrong*.

Any ideas?

Nazzer

---

### Post by nazzer on 2007-04-28
Solved it! Cleared my cache - and hey presto, I now have IPv6 access from the browser.

Summary:
IPv6 was enabled by default in Feisty, but the tunnel was temporarily down.
'IP a' told me what my interfaces were... fe80 address indicated local ipv6 connection;
browser needed its cache flushed to find sites that had different AAA and AAAA records ie v4 and v6

thanks all - now to create a suitable application to make IPv6 fun for others!

Nazzer
:-)

---

