---
title: "Screen Resolution"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Mohit on 2006-11-12
Hi

While running in WindowsXP,
I can change the screen resolution
but while working in Linux, 
The screen resolution is fixed to (640*480) 
How can i change this resolution,
Linux doesnot allow to change through, System>Prefrences>Screen resolution.

Please help
Mohit

---

### Post by taurus on 2006-11-12
You can reconfigure your X again from a terminal, Applications -> Accessories -> Terminal,

```
sudo dpkg-reconfigure xserver-xorg
```
You also need to install a driver for your graphic card.

---

