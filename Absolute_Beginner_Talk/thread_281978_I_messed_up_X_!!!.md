---
title: "I messed up X !!!"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by Dual Cortex on 2006-10-21
Anyway I stupidly (got its so embarrassing) tried to remove beryl and uninstalled all of this:
xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald-themes
obviously my X got trashed. I reinstalled those files even did a reinstall of ubuntu-desktop and X does not start up, gives me an error as if my xorg.conf was messed up. I've already reconfigured my xorg.conf two times with no good results. (i also used a xorg.conf backup and it did not work, I have another older backup yet to try)

Any ideas? thanks

---

### Post by taurus on 2006-10-21
You already tried

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by jordanmthomas on 2006-10-21
Also, could you post 
```
cat /etc/gdm/gdm.conf-custom
```
I have a sneaky feeling it's been customized to use XGL instead of a normal X

---

### Post by Dual Cortex on 2006-10-21
As I said, yes. I pretty muched [ENTER]'d my way through it.

---

### Post by Dual Cortex on 2006-10-21
> **jordanmthomas said:**
> Also, could you post 
```
cat /etc/gdm/gdm.conf-custom
```
I have a sneaky feeling it's been customized to use XGL

oh god.... that should be it!
dam it....
Let me try

---

### Post by Dual Cortex on 2006-10-21
yeah that was it... now I got to try to find that othe r backup
thanks for your help

---

### Post by jordanmthomas on 2006-10-21
no problem...I just wish you hadn't uninstalled beryl.  It's so fun!

---

