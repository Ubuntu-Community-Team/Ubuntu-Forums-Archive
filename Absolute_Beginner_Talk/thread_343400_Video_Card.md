---
title: "Video Card?"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by pissedoffdude on 2007-01-21
Well I decided to put ubuntu on my laptop but their is one problem.  I have an Nvidia geforce go 6150.  I can't boot into it using regular mode but I can using safe graphics mode.  So I booted into it in safe graphics mode.  I installed it but now when try to sign in it has a problem starting x.  It takes me to a white screen and it sems like it freezes.  Ive tried other distros such as sabayon that contain the closed source nvidia drivers and they seem to go fine.  Is their a way I can install these using the recovery mode?  Thanks

---

### Post by pissedoffdude on 2007-01-21
anyone?

---

### Post by taurus on 2007-01-21
From a recovery mode, run

```
dpkg-reconfigure xserver-xorg
startx
```

---

### Post by r4ik on 2007-01-21
Nice marker congrats !

---

