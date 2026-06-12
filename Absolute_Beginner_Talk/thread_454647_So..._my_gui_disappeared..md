---
title: "So... my gui disappeared."
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-05-25
I used the Feisty Fawn how-to guide to install Nvidia drivers. My monitor is 22 inches, with a native resolution of 1680x1050.

Now that I followed that how-to guide, when I boot up it looks like I'm in some kind of ms-dos. Black screen with white text.

What now?

---

### Post by taurus on 2007-05-25
What happens if you run this after you log in?

```
startx
```
And if you need to reconfigure your X again, try

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Mazen on 2007-05-25
Did u try ```
startx
```
maybe you are booting in the Recovery Mode

---

### Post by Mazen on 2007-05-25
oops sorry i didn't see the reply!!! i was on the reply page for 2 hours!!!!
hope it got u working

---

