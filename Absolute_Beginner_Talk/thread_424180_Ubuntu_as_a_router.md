---
title: "Ubuntu as a router?"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Shiner on 2007-04-26
I am preparing to do a clean install of either 6.06 or 7.04.
Does anyone know if Ubuntu can be set up to act as a router.  If so, can either the desktop or the server installs do this?
 
I'm not sure yet what I'll end up using the machine for, mostly to familiarize myself with it, I imagine.  Suggestions on which install would be best?

---

### Post by K.Mandla on 2007-04-26
Yup, you can set it up as a router. If that's the only thing it will do, you could probably start with a server installation (or just a command-line installation from the alternate installation CD). If you plan on using any kind of graphical desktop at all, you'll have to think about how to balance that against the workload.

---

### Post by Shiner on 2007-04-26
Yes, I would be using a graphical interface.  I'm not yet proficient enough to use command line only.  The routing workload would be pretty lite.  It would only be used when I was using a work PC from home.
 
My reason to have ubuntu as a router is so I don't have the cash outlay for a hardware router.  My home network is, of course, not a subnet of the office network.  I have an office PC at home to work-at-home with.  This PC is on the office windows domain and I run my own windows domain at home.  I have a hardware based VPN to the office.  So, my thought is... ubuntu routing the work PC traffic through my home network router over the VPN to the office.
 
Sound doable?

---

### Post by firefly2442 on 2007-04-26
Not to plug other topics or anything but smoothwall might also work:

[http://www.smoothwall.org/](http://www.smoothwall.org/)

I haven't used it before but apparently you just burn the ISO and install it.  Then you can configure it through a web browser.

Good luck with the project. :)

---

### Post by Shiner on 2007-04-27
> **firefly2442 said:**
> Not to plug other topics or anything but smoothwall might also work:
 
[http://www.smoothwall.org/](http://www.smoothwall.org/)
 
I haven't used it before but apparently you just burn the ISO and install it. Then you can configure it through a web browser.
 
Good luck with the project. :)
 
Looks like it would work well...if I were after a firewall.  ;)   Thanks for the suggestion though.  It's definately something to keep in mind.

---

### Post by compmodder26 on 2007-04-27
It is useful for a router as well.  Here is a tutorial I found on it: **edit: bad link, didn't detail on how to set it up as a router.  But it can be done.**

I would recommend using smoothwall or a similar dedicated distribution.  It will be much easier than setting it up from Ubuntu.

---

