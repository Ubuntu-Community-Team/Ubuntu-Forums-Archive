---
title: "Messed up my ubuntu-desktop somehow while removing Gaim (Ubuntu Studio)"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by kukuku on 2007-07-18
I saw some similar threads, but I don't want to try their solutions because Ubuntu Studio (7.04) seems to give it a different spin. How I arrived to the problem:

-Removed Gaim, which removed my ubuntu-desktop
-Automatic updates wails about partial upgrade and how it can't guess meta-package
-Reinstalling with sudo aptitude install ubuntu-desktop brings the following

```
The following packages have unmet dependencies:
  ubuntustudio-sounds: Conflicts: ubuntu-sounds but 0.6 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
ubuntustudio-desktop
ubuntustudio-sounds

Downgrade the following packages:
ubuntustudio-artwork [40 (feisty, feisty, now) -> 39 (feisty)]

Leave the following dependencies unresolved:
bsh recommends xlibs
Score is -942
```

Somehow I can't quite decide what's the best option here. I'd love for the automatic updates to stop giving the error message about ubuntu-desktop, but I wouldn't want to lose packages like ubuntustudio-sounds. Perhaps even attempt to finally get Pidgin installed. Does anyone know what I should do about this and not break everything?

---

### Post by shearn89 on 2007-07-18
could you not let it do the automatic "fix", and then reinstall ubuntustudio-sounds?

---

### Post by kukuku on 2007-07-18
This is one option. However, will the unresolved dependencies cause any problems?

---

