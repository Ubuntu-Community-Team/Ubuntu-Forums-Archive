---
title: "[SOLVED] gOS - DPKG error."
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by skymera on 2008-03-04
im trying to

sudo dpkg-reconfigure xserver-xorg 

on my laptop, but it comes up with an error, im not a new linux user and have fixed a fair share of problems but this has me stumped.

```
 scott@scott-laptop:~$ sudo dpkg-reconfigure xserver-xorg
dpkg-query: parse error, in file `/var/lib/dpkg/availible' near line 1: field name
/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed 
```

well it is, apt-get installed xserver-xorg says its latest.

anyone know what that erorr means or how to fix?
im in command line only.

---

### Post by MasterJS on 2008-03-04
try starting xorg before hand. ```
startx
``` While in command line and then do the reconfigure

---

### Post by kellemes on 2008-03-04
Try the following..
```

sudo dpkg --clear-avail
sudo apt-get update

```

---

### Post by skymera on 2008-03-04
got x working from the Vesa driver.

but still same error.

---

### Post by skymera on 2008-03-04
> **kellemes said:**
> Try the following..
```

sudo dpkg --clear-avail
sudo apt-get update

```

dude, i love you!
it worked, thanks so much

---

