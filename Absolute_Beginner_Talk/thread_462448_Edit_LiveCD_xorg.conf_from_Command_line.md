---
title: "Edit LiveCD xorg.conf from Command line"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by oli888 on 2007-06-02
On the LiveCD, how do you edit the xorg.conf from the command line?

Thanks,

Oli

---

### Post by annda on 2007-06-02
just like on an install

```
gksudo gedit /etc/X11/xorg.conf
``` for GUI

```
sudo nano /etc/X11/xorg.conf
```

or

```
sudo vim /etc/X11/xorg.conf
```

- whichever editor you use

---

