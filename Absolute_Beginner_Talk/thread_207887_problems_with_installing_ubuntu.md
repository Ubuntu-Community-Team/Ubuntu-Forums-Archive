---
title: "problems with installing ubuntu"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by mikolayek on 2006-07-02
hello!
I've got problem with my X server. I've installed Ubuntu, restart PC and after Ubuntu starts daemons (before login screen) starts X server, screen is going black, and stops.
What should I do with that?
Please help me.

---

### Post by taurus on 2006-07-02
You can either get into a console, <Ctrl><Atl>F2, and edit your /etc/X11/xorg.conf.  Replace whatever the driver is right now with "vesa".  Then, install the right driver for your video card...
```

sudo nano /etc/X11/xorg.conf

```
Now, it should look something like
```

Driver                  "vesa"

```
Or from a console, reconfigure your X again with
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by mikolayek on 2006-07-02
Hi!
After your advices it works :)
Thanks.

---

