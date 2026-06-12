---
title: "[SOLVED] Open drop down menus in terminal"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Wylkar on 2008-01-20
I enabled a feature in restricted drivers (in the administration menu) now I cannot get back into my desktop I can only get into shell (terminal) I was wondering if there was a way to deactivate this feature from the shell.

---

### Post by LaRoza on 2008-01-20
> **Wylkar said:**
> I enabled a feature in restricted drivers (in the administration menu) now I cannot get back into my desktop I can only get into shell (terminal) I was wondering if there was a way to deactivate this feature from the shell.

What driver?

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

This will allow you to reconfigure the video settings, if that is the problem.

---

### Post by Wylkar on 2008-01-20
thank you it is now working
(it was the ATI accelerated graphics driver)

---

