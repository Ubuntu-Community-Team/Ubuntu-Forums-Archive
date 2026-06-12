---
title: "&quot;Archive type not supported.&quot;"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by HaemoLacria on 2008-03-03
I want to open a .rar file with Archive Manager but it gives an error and says: Archive type not supported.

---

### Post by sailor2001 on 2008-03-03
in synaptics: download UNRAR

---

### Post by HaemoLacria on 2008-03-03
How can I download it easily?

---

### Post by mikewhatever on 2008-03-03
sudo apt-get install unrar.

---

### Post by HaemoLacria on 2008-03-03
sudo apt-get install unrar
Reading package lists... Done
Building dependency tree... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

---

### Post by sailor2001 on 2008-03-03
in synaptics: there is unrar free and unrar non-free.. install from synaptics and you get all your dependencies

---

### Post by SunnyRabbiera on 2008-03-03
right, synaptic package manager is the easiest way to download it

---

### Post by mikewhatever on 2008-03-03
> **sailor2001 said:**
> in synaptics: there is unrar free and unrar non-free.. install from synaptics and you get all your dependencies

If the package is not available through the repositories, it would not show in synaptic.

HaemoLacria, unrar package is in Multiverse repository, so make sure it is enabled under System>Administration>Software Sources.

---

### Post by zvacet on 2008-03-03
You don´t have all repos open.Go tot the** system>admin>software sources**>check all boxes under ubuntu software and updates tab.Reload.

```
sudo apt-get install rar unrar p7zip p7zip-full
```

When you have thesee installed just right click on rar file and select **unpack here.**

---

