---
title: "router / DSL modem problem"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by jbutler12 on 2007-01-06
Hi,

ops feel free to remove this as it isnt really an ubuntu question.  I didnt really know who else to ask though since this community has been really helpful i figured i would give it a shot.

I have a PC running ubuntu with wireless.  My wireless router is a D-Link 514+.  The wierdest thing is happening.  When i have my BellSouth Netopia DSL modem plugged into my router, my DSL connection goes down (like, not just that i cant surf, the "DSL Connected" light goes out and it is no longer on the bellsouth network).  When i plug my laptop straight into the modem, it works great.  I understand that a misconfigured router could make it impossible to surf the net, but what would make a router disconnect the DSL altogether (there is a "internet" light so i dont think that the DSL light = connected to internet).

Im a bit stumped here on what a router could do to kick a mdoem off a DSL network.

-John

---

### Post by teaker1s on 2007-01-06
unless the router is causing packet loss for some reason

---

### Post by HereInOz on 2007-01-06
A bit of a long shot here.  I wonder if the external (WAN) address of the router is hard coded or is assigned by DHCP?  If it is hard coded, and is the same as the internal (LAN) address of the modem, it could be causing all sorts of stuff.

Probably miles off the mark, but it is perhaps worth checking if you haven't already.

Also, on another tack, is the modem set up to provide DHCP services, or not?

Sorry I can't offer much more.

---

