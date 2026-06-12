---
title: "When i start screen saver in full screen mode, picture flickers a lot."
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by richard.stallman on 2008-02-21
When i open pictures in full screen mode/ start screen saver in full screen mode, the picture flickers a lot. How to solve this??

---

### Post by freelinuxhelp on 2008-02-21
Hi Richard Stallman! LOL!

When this happened to me, the problem was refresh rate. You might want to check on that.

---

### Post by richard.stallman on 2008-02-21
> **freelinuxhelp said:**
> Hi Richard Stallman! LOL!

When this happened to me, the problem was refresh rate. You might want to check on that.
how?

---

### Post by metallicamaster3 on 2008-02-21
Could indicate that you aren't using the appropriate driver for your graphics card, or incorrect values in your xorg.conf file, among other possibilities. 

Try tweaking with display and screen saver settings. Then, check your Xorg configuration file, considering perhaps reconfiguring Xorg from scratch.

---

### Post by Joeb454 on 2008-02-21
Do you have anything particular running such as conky that refreshes a lot?

I sometimes have that issue

---

