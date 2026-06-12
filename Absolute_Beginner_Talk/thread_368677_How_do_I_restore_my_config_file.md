---
title: "How do I restore my config file?"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by tomco on 2007-02-23
after trying to config my video card and restarting I got the "failed to start the x server" message. I tried through recovery mode to reconfigure but cannot get it right. I would like to go back to at least having something so how do I restore my backup which i noted was at:  /etc/X11/org.conf.70070223204617.

I tried just typing this at the root prompt - with sudo - but "no such command"

---

### Post by taurus on 2007-02-23
Try

```
cp /etc/X11/org.conf.70070223204617  /etc/X11/xorg.conf
```
Reboot and see if X is working again.

---

### Post by po0f on 2007-02-23
tomco,

Are you sure this file is a backup of your xorg.conf?  If you are, this should restore it:

```
[FONT="Courier New"]$ sudo mv /etc/X11/org.conf.70070223204617 /etc/X11/xorg.conf[/FONT]
```

To reset xorg.conf, run:

```
[font="Courier New"]$ sudo dpkg-reconfigure xserver-xorg[/font]
```

---

### Post by tomco on 2007-02-23
thanks, dont mean to be stupid but where do I type this - via the recovery mode?

---

### Post by taurus on 2007-02-23
Yip.

---

### Post by tomco on 2007-02-23
Thanks guys, worked a treat - now have screen resolution options - not sure how I managed, but what the hell...

---

