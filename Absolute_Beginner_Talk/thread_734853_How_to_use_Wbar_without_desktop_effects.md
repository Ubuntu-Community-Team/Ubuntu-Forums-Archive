---
title: "How to use Wbar without desktop effects?"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-03-25
I installed wbar and found that it can be used only when desktop effects are enabled. How to use it without desktop effects or is there any replacement for that?

---

### Post by Squish on 2008-03-25
replacement for wbar?
ever tried avant window navigator?

---

### Post by erginemr on 2008-03-25
Are you not able to use desktop effects (i.e. 3-D binary driver for your graphics card)? Or you don't want to?

---

### Post by adi_das on 2008-03-25
If i enable desktop effects my system becomes slow.

---

### Post by adi_das on 2008-03-25
want any program like awn or wbar without using compositing manager(compiz,beryl)

---

### Post by angry_johnnie on 2008-03-25
Neither beryl nor compiz fusion are absolutely necessary.  I've been using kiba-dock in fluxbox, with xcompmgr.  It should be in your repositories.

Just install it and then run

```
xcompmgr -c & disown
```

Then you can activate your dock. :-)

---

### Post by erginemr on 2008-03-25
> **angry_johnnie said:**
> Neither beryl nor compiz fusion are absolutely necessary.  I've been using kiba-dock in fluxbox, with xcompmgr.  It should be in your repositories.

Just install it and then run

```
xcompmgr -c & disown
```

Then you can activate your dock. :-)

I would just suggest xcompmgr, I am getting older ;)

Alternatively, if you want to have compositing on a larger scale, you may give a try to this link:
[http://ubuntuforums.org/showthread.php?t=648364](http://ubuntuforums.org/showthread.php?t=648364)

which involves the installation of a later metacity version either by compiling or by using the Debian packages given. 

As a matter of fact, metacity in Hardy Beta is a later version than the one in Gutsy and has compositing capabilities, which can be enabled by:
```
Alt+F2 -> gconf-editor -> /apps/metacity/general/compositing_manager
```
I don't know how it will perform in your system though.

A third option is to adopt xfwm (xfce's window manager) into Gnome, which may perform better:
[http://ubuntuforums.org/showthread.php?t=610606&highlight=xfwm+compositing+gnome](http://ubuntuforums.org/showthread.php?t=610606&highlight=xfwm+compositing+gnome)

but the above technique is still preferable as it involves the native window manager of Gnome.

---

