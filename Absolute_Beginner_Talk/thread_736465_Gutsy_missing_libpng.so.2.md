---
title: "Gutsy: missing libpng.so.2"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by johann_p on 2008-03-26
I have installed a precompiled linux program and now I get the error message:
> error while loading shared libraries: libpng.so.2: cannot open shared object file: No such file or directory

How can I get this file?

---

### Post by jan quark on 2008-03-26
try this in terminal
```

sudo apt-get install libpng12-0 libpng12-dev
```

which program did you install and how?

---

### Post by SunnyRabbiera on 2008-03-26
It might be the wrong version in your system, where did you get this package?

---

### Post by johann_p on 2008-03-26
> **jan quark said:**
> try this in terminal
```

sudo apt-get install libpng12-0 libpng12-dev
```which program did you install and how?
These packages are already installed. 

[http://www.radagast.se/othello/download3.html](http://www.radagast.se/othello/download3.html)

---

### Post by Bachstelze on 2008-03-26
This version of libpng doesn't exist in Ubuntu. I suggest you try to get a package for Ubuntu, or compile your app yourself.

---

### Post by Bachstelze on 2008-03-26
> **johann_p said:**
> These packages are already installed. 

Try this then, but you can consider yourself lucky if it works :

```
cd /usr/lib
sudo ln -s libpng12.so.0.15.0 libpng.so.2
```

---

### Post by SunnyRabbiera on 2008-03-26
If that is the case care to inform us about the application you installed, we cant help you unless we know what you did.

---

