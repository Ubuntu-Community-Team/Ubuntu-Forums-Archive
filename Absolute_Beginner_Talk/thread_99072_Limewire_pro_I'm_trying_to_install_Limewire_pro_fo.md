---
title: "Limewire pro I'm trying to install Limewire pro for linux how"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by tron1980 on 2005-12-04
Hello, I'm trying to install Limewire Pro in Ubuntu linux but can't for some reason. how do I complete this task.  Also How do I do this  "Open a shell and cd (change directory) to the directory where you downloaded the installer. At the prompt type: sh ./LimeWireLinux.bin

---

### Post by Qrk on 2005-12-04
"Open a shell" by

Applications-->accessories-->Terminal

To move to where you downloaded it type

```
cd /path/to/folder
```

Then you can type

```
sh ./LimeWireLinux.bin
```

Beware... Limewire needs Java to run. These forums have a ton of info on Java; just do a search.

---

### Post by sevenrechlin on 2005-12-05
Don't know how you obtained a .bin file, because when installing limewire pro you should've downloaded the file "limewirelinux.rpm" in which you would just need to "sudo alien limewirelinux.rpm" and then sudo dpkg -i the result.

---

