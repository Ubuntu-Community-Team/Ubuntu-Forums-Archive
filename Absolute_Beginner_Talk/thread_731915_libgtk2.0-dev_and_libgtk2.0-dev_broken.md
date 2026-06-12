---
title: "libgtk2.0-dev and libgtk2.0-dev broken"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by safe0495 on 2008-03-22
Libgtk2.0-dev and bin are broken. Synaptic doesn't want to fix it and i'm a total noob and tried everything (i think) and can't fix it. Anyone plz help!!

---

### Post by StOoZ on 2008-03-22
what do you mean by 'broken'?
what are you trying to do?

---

### Post by zvacet on 2008-03-22
```
sudo apt-get update && sudo apt-get upgrade
```

Post output here.

---

### Post by fela on 2008-03-23
I suggest reinstalling them by booting into recovery mode (if you can't goto gui cause gtk is 'broken'), type the root password when it prompts, then ```
apt-get --reinstall install packagenames
``` that should reinstall the 'broken' packages. (replace 'packagenames' with the packages that are 'broken', separated by spaces)

---

