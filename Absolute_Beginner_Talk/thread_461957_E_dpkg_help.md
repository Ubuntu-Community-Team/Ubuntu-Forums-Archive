---
title: "E dpkg help"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by jazzman84116 on 2007-06-02
How would I fix this





  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by celticbhoy on 2007-06-02
What happens when you rty and run 'sudo dpkg --configure -a' from a terminal window ???

---

### Post by overdrank on 2007-06-02
> **jazzman84116 said:**
> How would I fix this





  E: dpkg was interrupted, you must manually run '[COLOR="Red"]dpkg --configure -a[/COLOR]' to correct the problem. 
E: _cache->open() failed, please report.

Hi open the terminal under applications,accessories, and fun the command *sudo dpkg --configure -a* And that should do it. Good luck!:popcorn:

---

### Post by Skrynesaver on 2007-06-02
dpkg is part of the package(installed applications) management suite.  It was interrupted when running so you need to reconfigure it.  Helpfully in order to do this you simply open a terminal (Applications>Accessories>Terminal) and type,
```
sudo dpkg --configure -a
```
as the error message suggests ;)

---

### Post by jazzman84116 on 2007-06-02
Thank you That fixed it

---

