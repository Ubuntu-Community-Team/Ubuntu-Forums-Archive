---
title: "Xserver crashes after dapper upgrade!"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by DSn0wMan on 2006-06-25
After upgrading through Update Manager, my system hung on shutdown. After restarting Xserver crashes with the following errors:

dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)
(EE) Failed to load module "fglrx" (module does not exist, 0)
(EE) No drivers available.

Does anyone know how to fix this?

---

### Post by DSn0wMan on 2006-06-25
Answered my own question.

dpkg-reconfigure xserver-xorg

It worked the third time with fglrx driver. The upgrade somehow got rid of the ATI proprietary driver. Go figure.

---

