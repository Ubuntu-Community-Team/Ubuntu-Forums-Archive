---
title: "Uninstall/install driver"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by panzerfaust on 2006-06-24
How do I remove the fglrx driver before I'm going to change to my ati card? (which doesn't work with fglrx)

---

### Post by Acesomeone on 2006-06-24
"If (for any reason) the fglrx install fails, you can revert to the Xorg driver by executing":

```
sudo dpkg-reconfigure xserver-xorg
```

and selecting the "ati" driver.

---

