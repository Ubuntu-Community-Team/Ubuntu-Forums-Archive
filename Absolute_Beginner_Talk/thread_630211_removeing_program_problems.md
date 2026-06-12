---
title: "removeing program problems"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by moondoggy17 on 2007-12-03
i'm trying to remove limewire from my computer but i can't find a uninstaller or delete the folder because it says i'm not allowed

---

### Post by PmDematagoda on 2007-12-03
How did you install Limewire?

---

### Post by moondoggy17 on 2007-12-03
i installed it using the GDebi Package Installer. downloaded the LimeWireLinux.deb file

---

### Post by ajgreeny on 2007-12-03
Try ```
sudo dpkg -r LimeWireLinux
```You must use just the package name, not all the info about version also shown in the deb file name, and make sure you get the case right in the name as well, as linux is case sensitive.

To remove it along with the config files it should be ```
sudo dpkg -P LimeWireLinux
``` instead.

---

