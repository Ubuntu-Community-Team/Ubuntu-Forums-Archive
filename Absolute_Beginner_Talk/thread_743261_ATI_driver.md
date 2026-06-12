---
title: "ATI driver"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by falonyn on 2008-04-02
Real quick, can someone tell me how to install the ATI graphics driver on a brand new install of Ubuntu Gutsy Gibbon. I have tried using the command on the wiki, but I got an error message "xorg-driver-fglrx is not enabled"

Please help.

---

### Post by spiderbatdad on 2008-04-02
```
sudo apt-get install xorg-driver-fglrx
```
Reboot. enable desktop effects in preferences>>appearances.
??

---

### Post by Hobo Joe on 2008-04-02
If that doesn't work, use Envy.

I have a link in my sig.

---

### Post by falonyn on 2008-04-02
> **spiderbatdad said:**
> ```
sudo apt-get install xorg-driver-fglrx
```Reboot. enable desktop effects in preferences>>appearances.
??

It said that it " Couldn't find package xorg-driver-fglrx"

---

### Post by falonyn on 2008-04-02
> **Hobo Joe said:**
> If that doesn't work, use Envy.

I have a link in my sig.

It says I need debhelper. I couldn't find that in the synaptic package manager and I tried installing it through the terminal and it came back:

"Package debhelper is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package debhelper has no installation candidate"

---

### Post by spiderbatdad on 2008-04-02
Sounds like your sources are not enabled...you need a working wired connection...
follow these instructions: [http://ubuntuforums.org/showthread.php?t=693309](http://ubuntuforums.org/showthread.php?t=693309)

---

