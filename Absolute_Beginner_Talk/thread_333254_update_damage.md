---
title: "update damage"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Bad Apple on 2007-01-07
okay, i have just installed a load of recommended updates for ubuntu through the system, and since that my automatix has decided is doesnt regognise my version of the OS, any ideas? all i want is the iLinux stuff!!

---

### Post by Bad Apple on 2007-01-07
anyone know of a work around to get iLinux into ubuntu?

---

### Post by Jussi Kukkonen on 2007-01-07
> my automatix has decided is doesnt regognise my version of the OS
You might want to ask at the Automatix forums.
> anyone know of a work around to get iLinux into ubuntu?
Link to the software in question might help as searching in google doesn't seem to really help...

---

### Post by 3rdalbum on 2007-01-07
To install iLinux the manual way:

```
sudo aptitude install banshee kino
```

If you're using Kubuntu or Xubuntu, it's:

```
sudo aptitude install banshee kino f-spot
```

---

### Post by arnieboy on 2007-01-07
> **Bad Apple said:**
> okay, i have just installed a load of recommended updates for ubuntu through the system, and since that my automatix has decided is doesnt regognise my version of the OS, any ideas? all i want is the iLinux stuff!!
post the result of the following:
```
cat /etc/apt/sources.list
```

---

