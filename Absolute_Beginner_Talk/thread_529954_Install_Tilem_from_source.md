---
title: "Install Tilem from source"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-08-19
I need to get Tilem running, a TI-83 emulator. I extracted the tar.gz and ran ./configure
I get the error
```
checking for gtk+-2.0 >= 2.4.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.4.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
```
I rarely compile from source, so a little help is needed. What do I need to do?

---

### Post by southernman on 2007-08-19
It's right there in the error you posted. Do first:
> whereis gtk
If nothing is found on your system then do:
> sudo aptitude install gtk

---

### Post by Ek0nomik on 2007-08-19
You probably just need the gtk-dev files.

```
sudo apt-get install libgtk2.0-dev
```

Cheers!

---

### Post by tdrusk on 2007-08-20
Okay. Since TilEm is an emulator, I need a ti-83 rom. I found one and put it in the directory, but it can't find it.

any ideas?

---

### Post by tdrusk on 2007-08-20
I would love to get it working, but I found my TI-83, so I don't need it anymore.

---

