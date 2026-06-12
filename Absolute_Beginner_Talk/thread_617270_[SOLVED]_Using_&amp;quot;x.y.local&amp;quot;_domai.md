---
title: "[SOLVED] Using &amp;quot;x.y.local&amp;quot; domain, aka &amp;quot;.local&amp;quot; as a top level domain, and network DN"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by dom on 2007-11-19
We were using [FONT="Courier New"]company.local[/FONT] as our lan domain and had issues.


The .local is essentially reserved, as I found to my chagrin.


When we booted up some ubuntu boxes we had lots of issue with dns, we could resolve (sometimes) '[FONT="Courier New"]machinex[/FONT]', but not '[FONT="Courier New"]machinex.company.local[/FONT]'


So, eventually I did some network snooping and noticed that the DNS requests for the '[FONT="Courier New"].local[/FONT]' domains were going via mDNS and not regular DNS.


mDNS basically is used with 'zeroconf', a thing to help folks use a lan without needing DHCP and DNS servers, it resolves link-local addresses via multicast 
- [[http://en.wikipedia.org/wiki/MDNS]](http://en.wikipedia.org/wiki/MDNS])


Also:
".local deserves special mention as it is required by the Zeroconf protocol. It is also used by many organizations internally, which will become a problem for those users as Zeroconf becomes more popular. Both .site and .internal have been suggested for private usage [instead], but no consensus has yet emerged." 
- [ [http://en.wikipedia.org/wiki/Top-level_domain](http://en.wikipedia.org/wiki/Top-level_domain) ]


"Avahi is a Zeroconf implementation for Linux and BSDs" 
- [ [http://en.wikipedia.org/wiki/Top-level_domain](http://en.wikipedia.org/wiki/Top-level_domain) ]


Basically, I disabled the Avahi daemon until we removed the .local usage from our network.


I noticed a script at [FONT="Courier New"]/usr/lib/avahi/avahi-daemon-check-dns.sh[/FONT] which I think is suppossed to check for [FONT="Courier New"].local[/FONT] usage, and disable avahi if it's in place. 

But it didn't seem to work for me for some reason, perhaps because we have no reverse DNS or some other configuration issue ?

Anyway, if anybody else out there is noticing funny issues with DNS from ubuntu and not other os's on your network, hopefully this is in some way helpful

---

