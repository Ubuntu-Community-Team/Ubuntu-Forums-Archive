---
title: "need to reconfigure"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by chadmichael on 2006-03-15
When I installed my system a while back, there was a configuration program that ran and set up stuff like the graphics card, and more.  I just upgraded to Hoary ( I think ) and it seems like I need to re-run that configuration program.  Its not the xconfig its a configuration for the whole ubuntu system.

Can anyone tell what this program was?
Can anyone point me to documentation on this program?

---

### Post by mlind on 2006-03-15
do you mean
```

sudo dpkg-reconfigure xserver-xorg

```

please remember to backup your /etc/X11/xorg.conf before doing this!

---

