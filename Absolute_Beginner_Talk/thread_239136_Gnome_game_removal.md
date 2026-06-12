---
title: "Gnome game removal"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by statue on 2006-08-18
Any way to get rid of the default games that come with gnome? I tried through synaptic package manager but i couldnt get rid of them without uninstalling the gnome desktop.

---

### Post by meng on 2006-08-18
The gnome desktop (ubuntu-desktop) is just a metapackage. It won't actually uninstall GNOME itself.

---

### Post by statue on 2006-08-18
what's a metapackage?

---

### Post by meng on 2006-08-18
Good question (*sigh*, no it really is a good question) here's my answer:
It's an easy way to install a whole bunch of packages. As an analogy (aysiu has a better one) - think of it as a box containing a whole bunch of components. It's an easy container if you happen to want a standard selection of packages. However, the box itself is nothing of substance.

Put in technical terms, ubuntu-desktop itself is an empty package. But it cites several other packages as dependencies. Hence when you remove one of the component packages, you have to get rid of ubuntu-desktop as well, because it is a dependency of that package. But ubuntu-desktop per se contains nothing of substance.

Put simply, GNOME will still be there. Don't worry too much about it.

---

### Post by statue on 2006-08-18
lol thanks meng

---

