---
title: "Getting Modem To Connect Once You See Desktop"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by CARSRTHEWORLD on 2006-03-14
Hi

I have a Sagem Fast 800 modem, for 2mb tiscali bb.

I have read how to set it up and Im going to be doing that soon.

But I was gfoing to ask, is there any way to make it connect as soon as the ubuntu desktop loads, automaticly???

Thanks

---

### Post by jobezone on 2006-03-14
Probably yes, but it depends on how you intend to set up the dialing part.
If you're going to configure the connection with **pppconfig**, then running pon (or pon *provider-name-you-specified*) will do the dialing and conecting.  You can then add the command to Desktop-->Preferences-->Session .
You can also install and use **gnome-ppp**, which may or may not have that option. If I remember right, there is a good page at [wiki.ubuntu.com](wiki.ubuntu.com) explaining how to set up a modem connection (search for modem).
Good luck!

---

