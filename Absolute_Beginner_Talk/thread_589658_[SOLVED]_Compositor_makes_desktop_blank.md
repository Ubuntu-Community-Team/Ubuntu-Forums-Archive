---
title: "[SOLVED] Compositor makes desktop blank"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Xoanan on 2007-10-24
Hi All

I just upgraded to Feisty and I enabled compositor.  As soon as I did that, everything went blank

I have an i810e video card(may or may not be compatible.  

As a result of this, I can now only log in as a secondary user; or as the primary in failsafe terminal

Any ideas on how to fix this issue from cli?:

Thanx

Xoanan

---

### Post by overdrank on 2007-10-24
> **Xoanan said:**
> Hi All

I just upgraded to Feisty and I enabled compositor.  As soon as I did that, everything went blank

I have an i810e video card(may or may not be compatible.  

As a result of this, I can now only log in as a secondary user; or as the primary in failsafe terminal

Any ideas on how to fix this issue from cli?:

Thanx

Xoanan

HI you can try this command
```
sudo apt-get remove desktop-effects
```

---

### Post by Xoanan on 2007-10-24
That would be fine, except I can only access terminal in failsafe mode.  Would that work?

---

### Post by overdrank on 2007-10-24
> **Xoanan said:**
> That would be fine, except I can only access terminal in failsafe mode.  Would that work?

Hi and it should (hopefully) :KS

---

### Post by Xoanan on 2007-10-24
I'lll let you know

---

### Post by Xoanan on 2007-10-24
Nope;  It told me that desktop-effects have not yet been installed.  anything else?

---

### Post by Xoanan on 2007-10-24
Aha! 

Found a work around;  I used the secondary user to execute a script to turn compositor off.  Now the primary is accessible now!

Thanx

Xoanan:popcorn:

---

