---
title: "&quot;make&quot; command not working"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by EleFlameMax on 2007-12-25
I've already installed *build essential*, and ./configure went fine, but when I type "make", it gives me this:

```
make: *** No rule to make target `/usr/lib/qt4.2.2/mkspecs/linux-g++/qmake.conf', needed by `Makefile'.  Stop.

```

---

### Post by Rocket2DMn on 2007-12-25
What exactly are you trying to install/make?

---

### Post by PmDematagoda on 2007-12-25
I think you may be missing the Qt dev files, but could you post what application you trying to compile?

---

### Post by EleFlameMax on 2007-12-25
I am trying to compile KToon, which is an animation program.

---

### Post by PmDematagoda on 2007-12-25
KToon is available in the repositories, you can simply install it using:-
```
sudo apt-get install ktoon
```

---

### Post by EleFlameMax on 2007-12-25
Awesome. But is that why it isn't available through source?

---

### Post by Rocket2DMn on 2007-12-25
ktoon is available in the universe repository.  Add the Universe and Multiverse repos from System->Administration->Software Sources then either install from synaptic or use apt-get from terminal
```
sudo apt-get update
sudo apt-get install ktoon
```

---

### Post by PmDematagoda on 2007-12-25
> **EleFlameMax said:**
> Awesome. But is that why it isn't available through source?

You can compile the source, but it is more difficult and also a little less reliable than installing it through the repositories.

---

### Post by Rocket2DMn on 2007-12-25
It would be available through source too, but it is much easier to use the repositories - it is easy to install and keep up to date.  There really isn't much point in tracking down your build errors if you can install it in a method that works.

---

### Post by EleFlameMax on 2007-12-25
Thanks guys.

---

### Post by PmDematagoda on 2007-12-25
Glad to help:).

Merry Christmas.

---

