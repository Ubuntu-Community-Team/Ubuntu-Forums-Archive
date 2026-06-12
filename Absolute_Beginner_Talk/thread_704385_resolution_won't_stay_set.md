---
title: "resolution won't stay set"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by flowevd on 2008-02-22
hi,

was having a great time with Ubuntu until I ran a fullscreen app in Wine the other day at 640x480 resolution.

When i quit wine my desktop remained at that resolution; I duly set it back using the 'screen and graphics' dialog, to my accustomed 1280x800.

When i rebooted i was stuck back into 640x480. I went into screens and graphics and i can no longer change the resolution. My laptop lcd panel (that's what it is) is listed as a 'plug n' play device' as before.

What can I do?

Thanks for your help

flowevd

---

### Post by taurus on 2008-02-22
Try reconfiguring X server again with

Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
You can restart X again with <Ctrl><Alt>Backspace.

---

### Post by flowevd on 2008-02-22
thanks, taurus, that worked a treat.  :-)

flowevd

---

