---
title: "Emerald won't go away"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Hybrid86 on 2008-01-03
I just installed emerald in gutsey to try it out and see how it was. It was a bit glitchy though and used up way too much memory, so I decided to go back to the old window manager... only I have no Idea how.
Emerald starts automatically when I boot up now, and there doesn't seem to be an option to switch back. Can anybody help me?

---

### Post by JillSwift on 2008-01-03
in a terminal window, type:```
metacity --replace
```

---

### Post by Hybrid86 on 2008-01-04
I inputed that in the terminal, but all it did was downgrade my visual effects setting to "none". When I bumped it back up to "custom", emerald came right back :(

---

### Post by perlluver on 2008-01-04
```
sudo apt-get remove emerald
```
Then Restart X.

---

### Post by Hybrid86 on 2008-01-04
I have to physically remove it to shut it off? There's no way to just switch back to metacity but keep emerald installed?

EDIT: Shouldn't I just uninstall it through synaptic, or is that not as through?

---

### Post by perlluver on 2008-01-04
> **Hybrid86 said:**
> I have to physically remove it to shut it off? There's no way to just switch back to metacity but keep emerald installed?

EDIT: Shouldn't I just uninstall it through synaptic, or is that not as through?

You can do that too, I tried to disable it myself but had to remove it.

---

### Post by RomeReactor on 2008-01-04
Hi. Try running:
```
gtk-window-decorator --replace
```

---

### Post by Hybrid86 on 2008-01-04
That worked. Thank you :)

---

