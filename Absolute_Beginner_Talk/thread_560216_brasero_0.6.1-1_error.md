---
title: "brasero_0.6.1-1 error"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2007-09-26
I am trying to load brasero_0.6.1-1~getdeb1_i386.deb, but I am getting a error message. gdebi shows an error:
> Error: Dependency is not satisfiable: libatk1.0-0
What does this mean?
I checked in Synaptic and it shows all files with the name libatk are loaded.
Any help would be appreciated.

---

### Post by mesilliac on 2007-09-26
It probably requires a newer version of libatk than is available in the ubuntu repositories. You can either try to find a newer version of libatk and install that (which might in turn have its own problems), use the older version of brasero that's available through synaptic, or wait until ubuntu 7.10 is released and upgrade. The new version of brasero is probably designed to fit in with the new GNOME 2.20 desktop.

---

