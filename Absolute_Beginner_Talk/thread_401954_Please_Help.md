---
title: "Please Help"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Mowcius on 2007-04-05
X server config

--------------------------------------------------------------------------------

part way through the x server config my computer is asking me what the desired default color depth in bits is

i selected 24

then it came up with a message at the bottom saying:

x server-xorg postinst warning: over possibly-customised configuration
file backup; in /etc/x1/xorg.conf. 20070404210759

it then came up with the command prompt

what do i do?

---

### Post by taurus on 2007-04-05
Does X working with your new config at all?  Otherwise, reverse back to the last working copy of xorg.conf.

```
sudo cp /etc/X11/xorg.conf. 20070404210759 /etc/X11/xorg.conf
```

---

### Post by Mowcius on 2007-04-05
i'll go and test that

---

