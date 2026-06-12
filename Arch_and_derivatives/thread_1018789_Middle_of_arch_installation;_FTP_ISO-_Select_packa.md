---
title: "Middle of arch installation; FTP ISO- Select packages step won't find any"
date: 2008-12-22
forum: Arch and derivatives
---

### Post by Redrazor39 on 2008-12-22
I'm in the select packages stage right now and no matter which mirror I use, the categories are either error or expected, rather than base, support, devel, or lib. I already partitioned my drive, so now I just have to do this. I've checked my Internet connection and the status shows 76% for wireless, which is what I normally have. 

Even

```
ping -c 3 www.google.com 
```
Worked. 

This is really weird. I don't know what to do; please help!

---

### Post by OutOfReach on 2008-12-22
Try unselecting packages, an retrying. I remember I had this same problem. A wise thing to do would be to make a list of the packages you unselected and install them when your Arch installation is complete.

Hope that helps.

---

### Post by Redrazor39 on 2008-12-22
Ok I unselected all the packages that say error or expected, then hit ok and tried again, but same problem :(

I have 80% wireless signal quality and can ping to websites, but select packages isn't working :(

---

### Post by Redrazor39 on 2008-12-22
Help!!! Someone!!! I'm still stuck!

---

### Post by Redrazor39 on 2008-12-22
Alright forget it. I'm just going to burn a regular cd instead of the FTP cd and do updates later

---

### Post by hrod beraht on 2008-12-22
> **Redrazor39 said:**
> I'm in the select packages stage right now and no matter which mirror I use, the categories are either error or expected, rather than base, support, devel, or lib.

You're not specifying *base, support, devel, or lib* in the mirror address, are you? The Arch mirror directories have the major divisions of *Core, Extra, and Community*.
For example: [[COLOR="Blue"]ftp://locke.suu.edu/linux/dist/archlinux/[/COLOR]]("ftp://locke.suu.edu/linux/dist/archlinux/")

[QUOTE=Redrazor39]I'm just going to burn a regular cd instead of the FTP cd and do updates later[/quote]
That works too ;)

Bob

---

