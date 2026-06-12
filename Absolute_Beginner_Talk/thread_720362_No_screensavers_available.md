---
title: "No screensavers available"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by kestrel1 on 2008-03-10
Anyone got any ideas why I haven't got any screensavers available on a new install of Ubuntu 7.10.
I have it installed on a couple other systems, but not come across this before.
When I go to the screensaver Preferences, the screensaver names are shown, but when you highlight any of them, you get no preview in the box next to the list & even if you click preview you just get a blank grey screen with the option to move through the savers or to exit fullscreen,

---

### Post by sayakb on 2008-03-10
> **kestrel1 said:**
> Anyone got any ideas why I haven't got any screensavers available on a new install of Ubuntu 7.10.
I have it installed on a couple other systems, but not come across this before.
When I go to the screensaver Preferences, the screensaver names are shown, but when you highlight any of them, you get no preview in the box next to the list & even if you click preview you just get a blank grey screen with the option to move through the savers or to exit fullscreen,

Looks like an OpenGL problem to me.. try this:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by kestrel1 on 2008-03-10
Thanks for the reply.
I have gone through the xserver reconfigure, but this made no odds.
I have just noticed that there a some screensavers installed, so I assume that the others are not present for some reason. Any way to install the missing screensavers?
Thanks

---

