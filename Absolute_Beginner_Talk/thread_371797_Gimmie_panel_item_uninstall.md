---
title: "Gimmie panel item uninstall"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by loyaleagle on 2007-02-27
Hello everyone;

I uninstalled "Gimmie", yet it still shows an Gimmie icon in the "Add to Panel" window. How can I manually go into a configuration file and remove it. What file is it?

Thanks, Loyaleagle:confused:

---

### Post by taurus on 2007-02-27
Did you try something like this from a terminal?

```
sudo aptitude --purge remove gimmie
```

---

### Post by loyaleagle on 2007-02-27
I tried and still have the Gimmie icon in my "Add to Panel" window.

sorry...

---

### Post by aidanr on 2007-02-27
did you restart gnome? if you did and it's still there look for this file and remove it /usr/lib/bonobo/servers/GNOME_GimmieApplet.server

---

### Post by loyaleagle on 2007-02-27
Worked perfectly....

You are AWESOME!

Thanks....!

I LOVE UBUNTU!!!!!!! Loyaleagle

---

