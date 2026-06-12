---
title: "Problem Loading Synaptic Manager"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Majorflam on 2008-01-25
When I try to load the synaptic package manager, I get this error:

> 
E: dpkg was interupted, you must manually run 'dpkg-configure-a' to correct

E: _cache->open() failed, please report


How do I correct this?

---

### Post by smurphy_it on 2008-01-25
You should have to type dpkg configure-a or sudo dpkg configure-a in a terminal window (Applications, accessories, terminal).

---

### Post by UltraMathMan on 2008-01-25
I was just checking dpgk --help and it might actually be ```
sudo dpkg --configure -a
```

-Hope this helps :)

---

### Post by Majorflam on 2008-01-25
It returned:

```

Setting up odbcinst1debian1 (2.2.11-16) ...

Setting up unixodbc (2.2.11-16) ...

Setting up gcc-3.3-base (1:3.3.6-15ubuntu2) ...
Setting up libstdc++5 (1:3.3.6-15ubuntu2) ...

Setting up firefox32 (2.0.0.11) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

Now that I have accessed the package it tells me that sun-java6-bin is broken. How would I repair that?

Thanks for the help, by the way.

---

