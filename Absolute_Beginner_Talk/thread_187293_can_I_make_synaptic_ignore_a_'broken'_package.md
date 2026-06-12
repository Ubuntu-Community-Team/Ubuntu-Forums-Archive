---
title: "can I make synaptic ignore a 'broken' package?"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by chameleon_789 on 2006-06-02
hello

I installed a .deb package using the --force-depends switch. It's working fine, but whenever I try using synaptic or aptitude it tries to force an uninstall. I thought about installing the packages it depends on but they're nowhere in the repository. Is there a way to make synaptic ignore the dependencys for that package?

---

### Post by chameleon_789 on 2006-06-02
I couldn't find anything on google about this, save compiling your own 'dummy package' (impossible without uninstalling the broken package(s). unless you are lucky enough to already have the tools), but searching my own hard drive gave me the answer eventually!

 For anyone who'd like to know, here's how to **"unbroken"** a package in synaptic / aptitude / apt-get, without uninstalling it.

First of all, make a note of the package you installed, and the package(s) it depends upon that give it a broken status. Say I forced an install of *apples*, which depends on the package *obsolete* which isn't in the repository :

In a terminal type
```
sudo gedit /var/lib/dkpg/status
```
search the file for *apples* until you find something like :

```
Package: apples
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 316
Maintainer: 
Architecture: i386
Source: applesauce
Version: 1.0.10-1
Depends: packageA, packageB, obsolete
Description: Apples on your desktop!
```

Remove *obsolete* from the Depends: row, save the file, and you're done. Hope this helps some people out :)

---

### Post by pdc303 on 2006-06-04
excellent. Thanks :)

---

