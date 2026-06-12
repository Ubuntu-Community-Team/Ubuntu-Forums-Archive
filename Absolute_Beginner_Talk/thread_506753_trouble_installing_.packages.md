---
title: "trouble installing .packages"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Luksion Knight on 2007-07-22
i try to install the packages for warzone 2100 and thunde and lightning, bu i get the following return error ```
myname@myname-desktop:~/Desktop$ package install Thunder\ And\ Lightning\ 070710.package 

(autosu-gtk:27316): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

# Preparing package: Thunder and Lightning                                      
# Checking for required C library versions ... failed
# FAIL: 
# Your copy of glibc, a core system library, is too old for this package.
# You need at least the following symbols in glibc: GLIBC_2.0.
# 
# This error normally means that whoever built the package did not build it correctly.
# Please report the contents of this message to the provider of this package, and
# ask them to rebuild it using apbuild.
# 
# Upgrading glibc is highly dangerous, so we recommend in this situation that you
# compile the app you want to install from the sources if possible. Sorry :(
FAIL: Unable to prepare package Thunder and Lightning.
```

it happens with both installers. can someone shed some light on this problem?

---

### Post by PandaGoat on 2007-07-22
Your version of glibc is outdated. 
```

sudo apt-get install libglib2.0-0

```
or whatever te newest package is.  Use synaptic to find out.

---

### Post by Luksion Knight on 2007-07-22
well it says i already have it, but the package files still aren't working.

---

