---
title: "Trouble installing Winff"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by Totz on 2008-04-09
When I download and run the app through Package Installer, it tells me "Only one software management tool is allowed to run at the same time" even though there are no others running, any advice? Thanks in advance

---

### Post by Totz on 2008-04-09
Now I tried to do a software update and I get the error
> 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What should I do? :o

---

### Post by erginemr on 2008-04-09
Well, I suggest you to do what has been suggested by the error message and run:
```
sudo dpkg --configure -a
```
from a terminal (Main Menu -> Apps -> Accessories -> Terminal).

---

### Post by Totz on 2008-04-09
Thanks I had tried that, same outcome. I figured it out though, I use MoBlock and for some reason the winff address is blacklisted :/ Thanks anyway

---

