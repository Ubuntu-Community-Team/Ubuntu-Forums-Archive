---
title: "how to uninstall programes from .deb"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-05-31
I understand the add/remove and synaptic stuff, but how to I uninstall a program I installed using a .deb package? and is there a way to make sure the dependancies are removed as well if they are not needed?

---

### Post by daimaru on 2007-05-31
```
sudo dpkg -r yourdebfile.deb
```

sry read install :)

you can run
```
sudo apt-get autoremove
sudo apt-get autoclean
```

which should remove packages that are no longer needed.

---

### Post by aysiu on 2007-05-31
If you manually installed a .deb, you should be able to use Synaptic to remove it.

---

### Post by FleetAdmiral74 on 2007-05-31
alright, thanks for the quick response!

---

