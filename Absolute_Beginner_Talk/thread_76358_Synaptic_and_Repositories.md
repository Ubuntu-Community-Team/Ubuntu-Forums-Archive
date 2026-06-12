---
title: "Synaptic and Repositories"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by czambran on 2005-10-15
When I open synaptic there are two categories that I don't know what they mean:
Installed(local or obsolete)
Not Installed (residual Config).

Can somebody explain what do those categories mean??


Does Breezy Badger has backports or an 'extra' repository?

---

### Post by manicka on 2005-10-15
Installed (local or obsolete) are packages that you download and install yourself with dpkg

---

### Post by manicka on 2005-10-15
Not installed (residual config) are packages that you've removed and have left behind some config information. In synaptic you have the option to remove or completely remove a package. the first option leaves behind some residual information and the deb package in the apt cache. These packages will appear here.

---

### Post by aysiu on 2005-10-15
[QUOTE=czambran]
Not Installed (residual Config).[/quote] My guess is that these are programs that used to be installed, but when they were uninstalled they weren't "completely removed," so the configuration file remained, even though the program is gone. When you mark packages, you can mark them for "removal" or "complete removal." Complete removal removes the configuration files as well.

> 
Does Breezy Badger has backports or an 'extra' repository? Follow these instructions:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

No backports yet, but extra repositories are there.

---

