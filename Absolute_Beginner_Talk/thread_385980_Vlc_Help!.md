---
title: "Vlc Help!"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by totalnub on 2007-03-16
for some reason i cannot install vlc. i had it installed on another ubuntu 6.10, but for some reason, it won't install on this one. 

from synaptic:
vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libiso9660-4  but it is not installable
 Depends: libtar  but it is not installable
 Depends: libvcdinfo0 (>0.7.23) but it is not installable
 Depends: libvlc0 but it is not going to be installed
 Depends: libxosd2 (>=2.2.13) but it is not installable

from add/remove:

Cannot install 'vlc'

This application conflicts with other installed software. To install 'vlc' the conflicting software must be removed before.

Switch to the advanced mode to resolve this conflict.

please help.

---

### Post by Kobalt on 2007-03-16
Can you please try to install it from the CLI, Aptitude will give you what package is actually conflicting maybe : 
```
sudo aptitude install vlc
```

---

### Post by steve101101 on 2007-03-16
```

sudo apt-get install -f

```

should get all the dependences needed for you. try it.

---

### Post by totalnub on 2007-03-16
well, i've switched to 64-bit edgy and getting everything set up is taking some time. i just went into add/remove and found vlc. seems that things are gonna work out. :) ty for your response.

---

### Post by steve101101 on 2007-03-16
oh yeah. i forgot it was there for you already. my mistake. im glad it working out.

---

