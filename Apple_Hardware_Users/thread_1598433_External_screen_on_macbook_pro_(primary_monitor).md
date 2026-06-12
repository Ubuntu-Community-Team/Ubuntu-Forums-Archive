---
title: "External screen on macbook pro (primary monitor)"
date: 2010-10-16
forum: Apple Hardware Users
---

### Post by sunstriker on 2010-10-16
Hi!

I've installed Ubuntu 10.10 on my Macbook Pro 5,5. Everything is running fine (thanks to the excellent docs from the community) with some tweaks. 
Just one thing bothers me: when I tell Nvidia X Server Settings that I want to use my external screen as primary screen it doesn't put the gnome panels to the other screen, well... sometimes it does after a couple times but most of the time it doesn't.
Second question: is there a way to automatically detect when I connect a monitor instead of going to the Nvidia settings? Just the way Mac OS X does?

Thanks!

---

### Post by sunstriker on 2010-10-17
update: I've learned that saving the config to xorg.conf works well. If the X server starts with the external monitor connected then this one is the primary monitor. When the X server starts without the screen connected, the built-in lcd is primary and only screen. I was afraid that without the monitor connected X Server would still make the secondary screen primary, rendering it unusable when booting without the screen connected. However, that's not the case.

Is there a way to detect the screens without restarting the X server or changing the settings in Nvidia control panel?

---

