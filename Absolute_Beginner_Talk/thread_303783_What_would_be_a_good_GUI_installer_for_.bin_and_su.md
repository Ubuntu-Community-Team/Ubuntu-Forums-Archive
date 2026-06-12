---
title: "What would be a good GUI installer for .bin and such?"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by ballad of false hope on 2006-11-20
I was wondering what a good GUI installer for .bin type files and .deb would be? Thanks for your input.

---

### Post by adamkane on 2006-11-20
.deb has gdebi.

.bin can be installed with a Nautilus-script:
```

#!/bin/bash
sudo ./$1

```Place script in /home/<username>/.gnome/nautilus-scripts, then make executable:
```

sudo chmod +x ~/.gnome/nautilus-scripts/*

```

---

### Post by CatKiller on 2006-11-20
[How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

