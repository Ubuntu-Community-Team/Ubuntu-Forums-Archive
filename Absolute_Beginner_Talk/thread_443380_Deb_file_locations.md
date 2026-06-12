---
title: "Deb file locations ?"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by MrKlean on 2007-05-14
If I run the deb files on my desktop.. use them on my laptop.. will it tell me if I need dependencies.. or does only source do that...and where are the deb files that get installed ??
Thanks ; )

---

### Post by Skrynesaver on 2007-05-14
Installing the deb directly rather than through a repositry means thar you don't get alerted to updates, if you have an unusual requirement enable all repositries in Synaptic and then reload and search for the package you require.
The inatalled debs are kept in /var/cache/apt/archives/

---

### Post by MrKlean on 2007-05-14
Thanks.. that answers my questions ; )

---

### Post by aysiu on 2007-05-14
I think gDebi actually integrates with the package manager and installs dependencies for you. Can someone else confirm?

---

### Post by Skrynesaver on 2007-05-14
It does install the dependencies, however as the deb isn't tied to a repositry can it provide update notification?

---

