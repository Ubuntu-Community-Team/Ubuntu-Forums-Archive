---
title: "upgrading from hoary to breezy"
date: 2005-09-17
forum: Absolute Beginner Talk
---

### Post by randlieb on 2005-09-17
i set up hoary with an install cd. how will i upgrade from hoary to breezy? can i do it via download? will it be a regulat type update through synaptic? does it save all my hoary settings and files (it better!)?

---

### Post by Leif on 2005-09-17
when breezy is released, follow this : [http://ubuntuguide.org/#upgradehoarytobreezy](http://ubuntuguide.org/#upgradehoarytobreezy). once you've edited your sources, it will be like a regular update, and all your data will be safe.

---

### Post by drummer on 2005-09-17
[QUOTE=randlieb]i set up hoary with an install cd. how will i upgrade from hoary to breezy? can i do it via download? will it be a regulat type update through synaptic? does it save all my hoary settings and files (it better!)?[/QUOTE]
 To upgrade to Breezy via download:```
sudo gedit /ect/apt/sources.list
``` and change every 'hoary' to 'breezy', then ```
sudo apt-get update
sudo apt-get dist-upgrade
```All your files should be preserved, but I'd back up important stuff anyway, just in case. I'd also wait until Breezy is released before you upgrade as it is still in testing and you will most likely encounter problems.

---

