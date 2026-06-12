---
title: "changing DNS and IP address"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by drhiii on 2008-03-11
I am not sure how to articulate this, but the scenario is... I have a friend who just set up an Ubuntu box under a DSL box.  The WAN address of course can change periodically.  Is there a way to have the Ubuntu box send the current IP address to a DNS server that would be reallocate itself to the IP address of the DSL box, so the server could be accessed via a DNS entry of some type?

Does this make sense?

---

### Post by kesman on 2008-03-11
I have a setting for dynamic DNS in my DSL-box itself, so I don't have to configure my ubuntu station at all, I just made it to use static IP under my LAN and the dsl box does all the work.

EDIT:
what I'm after with this post is that maybe your friend has an option to use dynamic dns straight in the box also.

---

### Post by louieb on 2008-03-11
Some routers such as the netgear wgr614 can be set up to use a service like dyndns.com.  Thats how in do it.  [Lou's Home Server Stuff]("http://louieb.isa-geek.net/")
There is also the package **ddclient** that does the same thing. There are other packages - do a Synaptic search on dyndns. Good Luck.

---

