---
title: "Need GUI on Server"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by turbobill on 2007-11-07
I have seen a command to install the GUI on server before but can't seem to find any reference to it now.

Could someone please provide?

Thanks,
Wm

---

### Post by Inxsible on 2007-11-07
you can install any gui depending on whether you want gnome, kde or xfce

```
sudo aptitude install ubuntu-desktop
```Just change ubuntu-desktop to kubuntu-desktop for kde and xubuntu-desktop for xfce. If you also want a graphical login then install the appropriate DM
gdm for gnome, kdm for kde

---

### Post by aysiu on 2007-11-07
Do you want a server but a graphical way to access it?

Or did you accidentally install the server version when you wanted a desktop?

---

### Post by turbobill on 2007-11-07
THanks a bunch.

---

### Post by turbobill on 2007-11-07
> **aysiu said:**
> Do you want a server but a graphical way to access it?

Or did you accidentally install the server version when you wanted a desktop?

The first one.  Thanks.

---

### Post by aysiu on 2007-11-07
> **turbobill said:**
> The first one.  Thanks.
Then installing *ubuntu-desktop* is a bit excessive.

Try this instead:
[http://psychocats.net/ubuntu/minimal#barebones](http://psychocats.net/ubuntu/minimal#barebones)

---

