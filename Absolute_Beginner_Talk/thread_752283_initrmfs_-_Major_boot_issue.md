---
title: "initrmfs - Major boot issue"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by harry rao on 2008-04-11
I'm using ubuntu 7.10 and i have absolutely no idea what i've done but whenever i attempt to boot into ubuntu the screen remains blank and when i run it through recovery mode it goes through several processes and finally i get (initrmfs), instead of the usual harry@harry-laptop $ command line...
could someone please provide a solution?

regards,

-harry.

---

### Post by spiderbatdad on 2008-04-11
If you can boot into recovery mode  and use ctrl-d or crtl-c to get a command prompt:
run ```
sudo dpkg-reconfigure xserver-xorg
```read the dialogues and try to answer each question carefully. Reboot.

---

