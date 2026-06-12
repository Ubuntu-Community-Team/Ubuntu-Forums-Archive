---
title: "[SOLVED] Remove meta-package but leave component packages alone?"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by getut on 2007-11-09
Is it possible to remove, or at least break the link to a meta-package without uninstalling any of its component packages?

I have installed ubuntustudio-graphics which carries scribus. I would like to basically break scribus free from ubuntustudio-graphics so I can uninstall scribus and install the 1.3.3.10svn version. I'm pretty sure I can make aptitude remove scribus by force, but doing it that way will always show a broken package for ubuntustudio-graphics.

Basically I want to use the meta package to get all the goodies on in one shot, but then break all ties to it after that so I can work with the component packages indivdually with only their own dependencies.

---

### Post by por100pre1 on 2007-11-09
Remove the scribus package, that will remove the ubuntustudio-graphics metapackage but it will keep other packages from the installation. You can verify using this command:

```
sudo apt-get -s remove scribus
```

Use apt-get or Synaptic, **don't use aptitude**.

---

### Post by getut on 2007-11-09
Yup.. that got it.... THANKS!!!!

---

