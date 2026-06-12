---
title: "A package must never be updated"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by LittleKoy on 2008-01-12
Hello, this is probably a very stupid for you, but it's quite bothering me ^_^"

I have a package that must not be updated, or it won't work on my pc. But Ubuntu always lsists it in the update manager, and I don't know how to tell the system that package must not be upgraded. Isn't there a blacklist or something like that?

---

### Post by GavinZac on 2008-01-12
Open synaptic
Select the package you want to lock
Click "Packages" on the toolbar
Select "Lock Version"

et voila! :D

---

### Post by Miademora on 2008-01-12
The short version afaik is in synaptic. Select the package and choose "Package->Lock Version" or something similar.

And the long version

[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin)

---

### Post by LittleKoy on 2008-01-12
Thank you!

---

### Post by GavinZac on 2008-01-12
> **LittleKoy said:**
> Thank you!

You could even press the little :KS medal :D

---

