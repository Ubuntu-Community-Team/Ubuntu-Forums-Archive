---
title: "Apple (CMD) Key when VNCing to OS X"
date: 2010-07-20
forum: Apple Hardware Users
---

### Post by mkfs on 2010-07-20
When connecting to OS X via VNC using a Linux VNC client (KRDC), the windows key does not get passed through to OS X as the Apple key (which is what would happen if the keyboard was plugged directly into a Mac).

Obviously this is because the window manager (E17) doesn't map the Windows key to anything.

The question, though, is which of the entries in /usr/share/X11/XKeysymDB should the key be mapped to?

I usually use XF86ApplicationLeft and XF86ApplicationRight for the two windows keys, but these don't translate to CMD in OS X.

---

### Post by mkfs on 2010-07-21
Found that the Apple key is really just Left-Alt, so there is no need to map the Windows key to something special just to use OS X via VNC.

That means I can keep the Windows key mapped to launch urxvt :)

---

