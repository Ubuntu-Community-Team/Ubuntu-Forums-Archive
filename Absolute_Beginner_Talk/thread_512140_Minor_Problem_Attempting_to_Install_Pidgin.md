---
title: "Minor Problem Attempting to Install Pidgin"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by B-777 on 2007-07-28
Trying to install pidgin, but this comes up...

```
configure: error:

You must have the GTK+ 2.0 development headers installed to compile Pidgin.
If you only want to build Finch then specify --disable-gtkui when running configure.
```

Where do I get the above or is it in the synaptic?

---

### Post by pyros on 2007-07-28
the easiest way to fix this, at least it should fix it, is to run:
```

sudo apt-get build-dep gaim

```
that will install the dependancies for gaim, which should work to compile pidgin.

---

### Post by Bachstelze on 2007-07-28
I don't use build-dep, as I've found it sometimes installs more stuff than is needed. I prefer to install all my dependencies manually. To install the GTK development files :

```
sudo apt-get install libgtk2.0-dev
```

---

### Post by B-777 on 2007-07-28
> **HymnToLife said:**
> I don't use build-dep, as I've found it sometimes installs more stuff than is needed. I prefer to install all my dependencies manually. To install the GTK development files :

```
sudo apt-get install libgtk2.0-dev
```

Thanks...I actually found this in the synaptic and installed it from there and now everything works.

---

