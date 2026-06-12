---
title: "Not sure where to put this - Router Trouble"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by The Joe on 2007-02-10
Well I've been with Ubuntu since the release of Edgy, and after two weeks I managed to install it on a friends computer (by request!). Unfortunately he's on a router.
Router + Linux = Disaster
So every time he runs Ubuntu, the whole network dies, IE: No one can use the internet in the house, this is pretty annoying because he's very keen with Ubuntu and wants to use it to it's full potential, can anyone think of a solution?
According to him, the router is Netgear.

---

### Post by ciscosurfer on 2007-02-10
> **The Joe said:**
> Well I've been with Ubuntu since the release of Edgy, and after two weeks I managed to install it on a friends computer (by request!). Unfortunately he's on a router.
Router + Linux = Disaster
So every time he runs Ubuntu, the whole network dies, IE: No one can use the internet in the house, this is pretty annoying because he's very keen with Ubuntu and wants to use it to it's full potential, can anyone think of a solution?
According to him, the router is Netgear.Go into System > Administration > Networking and make sure all the settings are correct.  The ethernet connection should most likely be set up as DHCP (there are of course other ways of doing this, but my setup is like this).  Next, log into the router and make sure all the settings in the router match up with the what is trying to be accomplished.  For example, you'll want to make sure the router is asking for an IP dynamically (again via DHCP), the DNS settings should also be getting grabbed from the ISP.  If you've set up the settings statically (only allowing a specific block of IP addresses) then make sure that one of those addresses correspond to the IP address range offered (that you set on the router) and set one of those IP addresses on your (his) Ubuntu box.

Hope this helps you guys out a bit. :-)

---

### Post by The Joe on 2007-02-11
Right I've passed the message on, I'll post again if theres any more problems, thanks a lot.

---

