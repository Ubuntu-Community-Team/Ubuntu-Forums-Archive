---
title: "Screen Resolution, Restricted Drivers"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2007-11-18
As soon as I enabled Restricted Drivers, my screen resolution wont go high up anymore.

What can I do to fix this?

---

### Post by DCM36 on 2007-11-18
For us to help you further, we're going to need to know what restricted drivers you installed (i.e. nVidia, ATI, etc.) and the display adapter in your computer. Also your current screen resolution and the one you are attempting to obtain could be beneficial.

---

### Post by Cheese Roller on 2007-11-18
NVIDIA accelerated graphics driver (legacy cards)

800x600 is my current.

1280x1024 is what I want.

---

### Post by Qwerty_ on 2007-11-18
Try this.

```
 sudo dpkg-reconfigure xserver-xorg
```

That should solve your problem.

---

### Post by Cheese Roller on 2007-11-18
Okay, it is asking me a lot of questions I don't understand.

---

### Post by shuttleworthwannabe on 2007-11-18
fill in most of the details (I left them as default ones) except where it asks you to select the screen resolutions (select ones that your screen permits, if max is 1280x1024, select that, and any other ones below that. The other tricky place is when it asks to detect screen, here I say no and it places a generic monitor; also select the controller correctly (in my case it is fglrx, am not sure what yours will be).

Reboot, and see what happens,

S

---

### Post by Qwerty_ on 2007-11-18
Make sure you select nvidia as your driver though and not nv.

---

