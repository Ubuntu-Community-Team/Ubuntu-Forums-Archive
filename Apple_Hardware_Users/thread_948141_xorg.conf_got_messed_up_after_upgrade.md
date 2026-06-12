---
title: "xorg.conf got messed up after upgrade"
date: 2008-10-14
forum: Apple Hardware Users
---

### Post by ciclopropano on 2008-10-14
I made back ups of my xorg.conf file, the problem is that I can't see anything! only the mouse moving around on an empty blue screen 
how can I get to a terminal?
please help, I'm new to linux!
I have an intel alluminium imac

---

### Post by cyberdork33 on 2008-10-14
Use CTRL+ALT+F1 to get to a console. You can login there, and nano to edit your file:
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by ciclopropano on 2008-10-15
that doesnt work because I had configured the F1 and F2 keys to set the screen brightness :(

---

### Post by cyberdork33 on 2008-10-15
> **ciclopropano said:**
> that doesnt work because I had configured the F1 and F2 keys to set the screen brightness :(

use the Fn key to switch the function of the F-keys

CTRL+ATL+Fn+F1

---

