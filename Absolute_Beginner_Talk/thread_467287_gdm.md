---
title: "gdm"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by ajeffreys on 2007-06-07
I had ubuntu running with the gdm, but then I also installed kde, and so now it has changed the login manager to kde's. How do i revert back to gdm?

---

### Post by steeleyuk on 2007-06-07
I presume you're talking about the Login screen theme. If you are anyway:

System > Administration > Login Window > Local tab

---

### Post by NeoLithium on 2007-06-07
Open up a terminal, and enter
```

sudo dpkg-reconfigure gdm

```

Allow it to set up and then select it as your manager :)

---

### Post by zvacet on 2007-06-07
On login screen in the bottom left corner you can** choose sessions**.Select GNOME.

---

