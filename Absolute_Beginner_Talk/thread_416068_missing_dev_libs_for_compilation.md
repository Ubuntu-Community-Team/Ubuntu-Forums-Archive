---
title: "missing dev libs for compilation"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by kabanta on 2007-04-20
For Feisty, I want to compile cvs version of emacs with gtk. after checking out emacs source:

```
./configure --with-gtk
```

The resulting error:

```
 [lots of stuff removed]
checking for gtk+-2.0 >= 2.4 glib-2.0 >= 2.4... no
Package gtk+-2.0 was not found in the pkg-config search path. 
Perhaps you should add the directory containing `gtk+-2.0.pc' to 
the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' 
found Package glib-2.0 was not found in the pkg-config search path. 
Perhaps you should add the directory containing `glib-2.0.pc' to
the PKG_CONFIG_PATH environment variable No package 'glib-2.0' found
```

I have not been able to find either gtk+-2.0 or glib-2.0

What dev packages are necessary to solve this dependency?

thanks.

---

### Post by taurus on 2007-04-20
You need the developing packages so either search for them in synaptic or do

```
sudo aptitude update
sudo aptitude install glib-dev libgtk-dev
```

---

### Post by kabanta on 2007-04-20
> **taurus said:**
> You need the developing packages so either search for them in synaptic or do

```
sudo aptitude update
sudo aptitude install glib-dev libgtk-dev
```

Thanks for quick reply. I tried that, but still same errors.

I only just discovered the advantage of aptitude over apt-get. Earlier I had installed gcc and build-essential with apt-get -- but then discovered that it was only possible to successfully install libgtk2.0-0-dev with aptitude. perhaps mixing the use of apt-get and aptitude is causing problems for me? If so, is there an easy alternative to re-installing Feisty and doing all additional package installs with aptitude?

thanks.

---

