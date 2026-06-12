---
title: "Super user?"
date: 2008-10-18
forum: Apple Hardware Users
---

### Post by Thwackum on 2008-10-18
So I just upgraded from gutsy on my PPC iBook G4.  I'm trying to finish dowloading my updates/install my wireless cards driver, but a window comes up saying that i need to manually install "dpkg --configure -a'.  I ty to load it in the terminal but it says i need super user privlages.

  please help

---

### Post by howefield on 2008-10-18
Preface the command with sudo

```
sudo dpkg --configure -a
```

That'll do it.

---

