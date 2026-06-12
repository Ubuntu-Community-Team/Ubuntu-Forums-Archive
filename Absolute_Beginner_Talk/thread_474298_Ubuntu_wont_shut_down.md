---
title: "Ubuntu wont shut down"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by fbformula on 2007-06-14
First of all sorry if this problem has already been posted and i just over looked it.  I've been trying for the past few days to install Ubuntu on one of my older PCs and i have had no problems except for this one. when i try to shut down my machine normally (via the button in the top right) it will not shut down entirely. It starts to shut down gets to the last loading screen the loading bar goes all the way across and than it just sits there and never fully shuts down unless i press the power button on my machine. Any help would be wonderful, thanks in advance.

---

### Post by Crafty Kisses on 2007-06-14
You should go into terminal and type:
```
top
```

See if there are any programs eating up resources, that's possibly causing it.

---

### Post by fbformula on 2007-06-15
It dosent look like theres any resource hogs running but thanks for the great command i dident know that one although is rather useful.

---

### Post by Crafty Kisses on 2007-06-15
> **fbformula said:**
> It dosent look like theres any resource hogs running but thanks for the great command i dident know that one although is rather useful.

You can also download a program called "Conky" which monitors all your CPU stats at all times.
```
sudo apt-get install conky
```

---

### Post by gammaknife on 2007-06-15
> **fbformula said:**
> It dosent look like theres any resource hogs running but thanks for the great command i dident know that one although is rather useful.

if you can't find any other solution, use sudo
 shutdown -h now. It's much faster than clicking on the logout icon anyway

---

### Post by fbformula on 2007-06-15
I tried useing the command shutdown -h now but it just took me to the same screen where it gets stuck

---

