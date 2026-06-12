---
title: "Is it possible to export a list of installed apps?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by arphaus on 2007-05-19
I'll be reinstalling to a new hard drive at some point, and I'll be saving my home directory so I can keep some of my files and settings.  I'd like to be able to reinstall apps easily - is there a way to export a list of what apps I have installed, or do I have to bust out some pen & paper.

Gracias!

---

### Post by Bachstelze on 2007-05-19
```
cd
dpkg -l > installedPackages.txt
```

done :)

---

