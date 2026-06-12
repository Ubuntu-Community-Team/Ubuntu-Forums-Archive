---
title: "Ubuntu not booting into GDM"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by prodigy6630 on 2008-04-18
Hi

I installed KDE4 on Ubuntu, yeah yeah, I know, what was I thinking :-)

Anyways, I removed it but now my Ubuntu is booting into terminal. How do I get it to boot back into GDM?

Thanks

---

### Post by doctorbighands on 2008-04-18
When you removed KDE 4, did you replace it with another GDM (older KDE, Gnome, XFCE, etc)? If not, then Ubuntu is booting to the command line because there's nowhere else to go! :)

If you did install a replacement GDM, then when it gets to the command line, try typing in
```
startx
```

---

### Post by angry_johnnie on 2008-04-18
Also, once you're in your graphical environment, go to system > administration > services, and make sure GDM is enabled.

---

### Post by louieb on 2008-04-18
For now try to start gdm by
```
sudo /etc/init.d/gdm start
```

Can't remember which run level is the default.  Think its rc2
Anyway to get it to start gdm automatically you need to add a symbolic link in directory /etc/rc2.d/ to /etc/init.d/gdn. 

I really need to write this stuff down. Maybe someone will come along and be more specific as to how to add the symbolic link. Good Luck.

---

