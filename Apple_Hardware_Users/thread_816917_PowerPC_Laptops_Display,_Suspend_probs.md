---
title: "PowerPC Laptops Display, Suspend probs"
date: 2008-06-03
forum: Apple Hardware Users
---

### Post by Scientia on 2008-06-03
Running Hardy on a PPC iBookG3 , vid card ATI Radeon Mobility M7 LW [Radeon Mobility 7500]. My suspend doesn't work, and the iBook brightness controls don't work. Maybe it's because they register as F1 and F2. I don't have the know-how to edit my xorg.conf anyhow, and as some others were having the same issue i thought some help would be good.

Thanks.

---

### Post by stream303 on 2008-06-03
To edit your /etc/X11/xorg.conf file you can do it via the terminal with the nano editor:

```
sudo nano -w /etc/X11/xorg.conf
```

(ctrl-o to write your changes out, ctrl-x to quit)

or if you want to do it graphically with ubuntu:
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Scientia on 2008-06-04
Yes, but theen anything on how to do the configs after that?
The last time i tried(from another post), i got a blank gedit window, and then my system froze.

---

