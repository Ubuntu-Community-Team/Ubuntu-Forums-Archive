---
title: "Saving X Configuration"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Ross M on 2008-01-27
Hello,

I have installed the nVidia drivers for my GeForce 8800 GTS.  However, I'm stuck at a very low resolution and I run 2x 22" Acer Widescreens and this is hard to work with as you might be able to tell.

When I open up my nVidia options and change the settings, I am unable to save my settings.

```
Failed to set MetaMode (1) 'DFP-0: 1680x1050 @1680x1050 +0+0' (Mode 1680x1050, id: 52) on X screen 0.
```

How can I fix this?

Thank you VERY much,
Ross M

---

### Post by bodhi.zazen on 2008-01-27
Perhaps run as root :

```
gksu nvidia-settings
```

---

### Post by Ross M on 2008-01-27
Still getting the same error and my second monitor isn't showing up when run as root.

> Failed to set MetaMode (1) 'DFP-0: 1680x1050 @1680x1050 +0+0' (Mode 1680x1050, id: 52) on X screen 0.

---

### Post by bodhi.zazen on 2008-01-27
Not sure then, that is a fairly new card, I suggest you search / post on the Nvidia forums, Linux section ...

---

### Post by Ross M on 2008-01-27
Yes but it doesn't look like the card is causing the saving problem...

---

### Post by bodhi.zazen on 2008-01-27
running as root allows you to edit / save /etc/X11/xorg.conf

so it can not be a permissions problem (unless you missed the "save" button).

---

