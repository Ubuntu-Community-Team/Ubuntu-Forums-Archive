---
title: "[SOLVED] Package manager questions"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by purdticker on 2007-06-21
Can anyone give me a short rundown on all the different package manager options available and how they differentiate from one another.

For example, I've seen references to:

dbk
aptitude
apt-get
apt-cache

I can find individual documentation for each, but not how they relate to each other.

---

### Post by PartisanEntity on 2007-06-21
The difference between aptitude and apt-get used to be that apt-get did not keep track of the dependencies it installed, so when you would remove an application you would end up with residual packages. However as of Feisty Fawn apt-get also keeps track of dependencies.

apt-cache is a command to obtain information about packages in the cache of apt.

Not sure what the 4th is.

---

### Post by NeoLithium on 2007-06-21
I'm guessing DBK would be dpkg, in which case that is the package manager that actually installs the .deb files onto your Ubuntu box.  When you use apt-get, aptitude, etc, they download .deb files and their required dependencies, then they use dpkg to install them for you. Kind of like a little assembly line, I guess.

---

### Post by purdticker on 2007-06-21
Ah ok that's exactly what I was lookin for thanks guys.

---

### Post by NeoLithium on 2007-06-21
You're very welcome :)

---

