---
title: "Limewire"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by steve-shinn on 2007-06-12
Hi,

Having tried Add/Remove Programs    Autamatix2  and Synaptic Package Manager I can find no references to being able to install Limewire (Only frostwire on synaptic)

Can anyone advise a Ubuntu newbie like myself, the easiest/most fail safe way of downloading and installing limewire on Feisty 7.04??

Thks in advance

SteveS

---

### Post by Pragmatist on 2007-06-12
Go to the limewire website and download the package for Debian/Ubuntu, then type this in the directory you downloaded it to (or, you can put it in a traditional place like /usr/local  however, in this case you need to run the following command with "sudo")

```
dpkg -i LimeWireLinux.deb
```

That should do it.

---

