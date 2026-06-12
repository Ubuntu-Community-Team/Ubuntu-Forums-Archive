---
title: "Disable tapping on Macbook Pro 5.5"
date: 2011-08-02
forum: Apple Hardware Users
---

### Post by Jaxilian on 2011-08-02
Hi,
I followed guide on [https://help.ubuntu.com/community/MacBookPro5-5/Natty](https://help.ubuntu.com/community/MacBookPro5-5/Natty)
but I cannot disable tapping no matter how I do it.

I tried System > Preferences > Pointing devices (also Mouse one)
and both unchecking "Enable mouse clicks with touchpad" and checking "Disable tapping"...doesn't work :confused:

I think that wiki needs and update cause there is way too many things are is not correct.

---

### Post by blane2 on 2011-08-02
update it then with new info and work arounds :D

---

### Post by Jaxilian on 2011-08-03
if I knew what to do then I probably would, but I have no clue

---

### Post by Jaxilian on 2011-08-05
Tried adding this to xorg.conf and /usr/share/X11/xorg.conf.d/99-multitouch.conf . Also tried them separately.

```
Option "TapButton1" "0"
```

but didn't work.

---

### Post by Jaxilian on 2011-08-15
*bump*

---

