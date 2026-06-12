---
title: "Uninstalling a package"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Vord on 2007-01-16
So, I installed the GAIM xfire plugin for dapper by mistake, and upon realizing my slip up, I downloaded the proper version, but can't install it until I remove the current installed package. Can somebody let me know how I would do this?

---

### Post by Vord on 2007-01-16
I attempted
```
sudo dpkg -r gaim-xfire_0.6.0-gaim1.5-etch1_i386

```
Which output
```
dpkg - warning: ignoring request to remove gaim-xfire_0.6.0-gaim1.5-etch1_i386 which isn't installed.

```

Though I'm sure that's the package that was installed.

---

### Post by Vord on 2007-01-16
Okay, well I just removed it through synaptic package manager.

Thanks anyway, I guess?

---

### Post by mcduck on 2007-01-16
if you want to use dpkg -r to remove a package you shouldn't use the whole name of the package file, just the actual name of the package. So in this case I suppose it would be 'sudo dpkg -r gaim-xfire' (or 'sudo apt-get remove gaim-xfire')

Anyway, Synaptic does exactly the same thing so it doesn't matter which way you do it :)

---

