---
title: "[SOLVED] Ubuntu rebooting after login"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by orrie on 2008-01-20
I have just logged in and then the computer reboots.
The only thing I can access is the recovery mode.

Someone been there and done that?

---

### Post by orrie on 2008-01-20
I solved this actually.

Just logging into recovery mode and wrote in terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

