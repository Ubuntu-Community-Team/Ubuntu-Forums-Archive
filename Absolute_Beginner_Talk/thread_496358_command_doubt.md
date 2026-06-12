---
title: "command doubt"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by desijays on 2007-07-09
Is there a way to find out what files a package is going to install on my system before i

sudo apt-get <packagename>

??

---

### Post by chuck_notorious on 2007-07-09
Maybe this is what you want:

apt-get install <package-name> -s

-s is for simulate

it will show you the list of packages it would download and then the list of dpkg operations it would perform to install and configure these packages without actually changing the system.

--Chuck.

---

