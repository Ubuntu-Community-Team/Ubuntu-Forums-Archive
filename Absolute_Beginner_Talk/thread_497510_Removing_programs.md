---
title: "Removing programs"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by yehoni on 2007-07-10
I'm trying to remove programs installed using the "make install" command, specifically Hamachi and gHamachi.  Is this possible, and does anyone know how to  do it?

---

### Post by zvacet on 2007-07-10
Go to the same folder in wich you type sudo make install and type

```
sudo make uninstall
```

---

### Post by destructchaos on 2007-07-10
it's just as simple as installing:

```
make uninstall
```

---

### Post by yehoni on 2007-07-10
Doesn't seem to work.  I just get

```
make: *** No rule to make target 'uninstall'.  Stop.
```

---

