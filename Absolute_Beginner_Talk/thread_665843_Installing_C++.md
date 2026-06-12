---
title: "Installing C++"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by addada on 2008-01-12
How do I install  C++ and work on it in UBUNTU Breezy? My work is  like installing a software by the name CLICK which is based on C++..

---

### Post by finer recliner on 2008-01-12
to compile C++ files you need GCC (GNU C++ compilers). it is included in the build-essentials package

```
sudo apt-get install build-essentials
```

---

### Post by taurus on 2008-01-12
> **finer recliner said:**
> to compile C++ files you need GCC (GNU C++ compilers). it is included in the build-essentials package

```
sudo apt-get install build-essentials
```

There's no [COLOR="Blue"]s[/COLOR] at the end of build-essential.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by Steveway on 2008-01-12
You can easily install the compilers with... what Breezy Badger?
That's ridicously old.
I would advise in updating to a more recent version of Ubuntu.
Are the Breezy Repos even still up now?

---

