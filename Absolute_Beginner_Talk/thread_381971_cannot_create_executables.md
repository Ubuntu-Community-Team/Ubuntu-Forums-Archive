---
title: "cannot create executables"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by paka_kro on 2007-03-11
I'm trying to install a package for the first time and I get this error:

checking for C compiler default output file name... configure: error: C compiler cannot create executables

directory is 
drwxr-xr-x

---

### Post by taurus on 2007-03-11
You need a build-essential package.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by PriceChild on 2007-03-11
```
sudo apt-get install build-essential
```This package is needed for all the basic tools :)

EDIT - Now I'm _*annoyed*_ taurus!!!

---

### Post by taurus on 2007-03-11
> **PriceChild said:**
> 
EDIT - Now I'm _*annoyed*_ taurus!!!

Hi, Pricey.  ):P

---

### Post by paka_kro on 2007-03-11
Ok, thanks.  got past THAT, but now looking for BISON.  BUT, what I'm trying to install is gstreams 'cause totem says I don't have a decoder to play my mp3.  Do I need another "aptitude" change, or a different decoder ring?

---

### Post by PriceChild on 2007-03-11
[uwiki]RestrictedFormats[/uwiki]

---

