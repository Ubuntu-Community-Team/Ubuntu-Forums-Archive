---
title: "Way to force a root file system check on reboot?"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by UberIcarus on 2006-10-18
Someone gave it to me in the IRC channel, but I'm currently unable to use IRC, and I didn't write it down.

thankyou in advance =)


Also, unrelated (but the reason I can't use IRC right now) does anyone know what this means (I've found no help in the man pages):

xlib: connection to "0.0" refused by server.
xlib: No protocol specified

I see no options in the man pages of either iwconfig or ifconfig to specify a protocol?

---

### Post by po0f on 2006-10-18
UberIcarus,

Someone [here](http://www.ubuntuforums.org/showthread.php?t=239622) came up with a way to do it.

[EDIT]

What IRC client are you using?  Is X started properly?  It has nothing to do with networking, unless you're networking your X connections.  ;)

---

### Post by UberIcarus on 2006-10-18
> **po0f said:**
> UberIcarus,

Someone [here](http://www.ubuntuforums.org/showthread.php?t=239622) came up with a way to do it.

[EDIT]

What IRC client are you using?  Is X started properly?  It has nothing to do with networking, unless you're networking your X connections.  ;)

Thankyou!, actually I'm using another (windows, and work) computer that I can't put IRC clients on, to ask my questions because I can't for some reason access the bloody wireless connection through my laptop because dhclient and wlassistant are saying the AP just refuses to communicate with me (despite being an open [purposely] wifi network). Grrr....

---

### Post by CatKiller on 2006-10-18
```
sudo touch /forcefsck
``` is another way to do it.

---

