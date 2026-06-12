---
title: "[SOLVED] Compiled Compiz Fusion myself but..."
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-10-23
I can't get it to run?

I get this error:
```

compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

```

It is Compiz Fusion 0.6.2 and I've never had any problems running CF on my i915....

I also used these instructions, but I'm on Feisty...

[http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html#comment-118]("http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html#comment-118")

---

### Post by Clay_Banger on 2007-10-24
try running it using this command:
```
compiz --replace ccp &
```

---

### Post by isaacj87 on 2007-10-24
Thank you for the response...Actually I figured it out my self...

I was also compiling the fusion-icon and found the instructions on the Forum and it detailed installing compiz-dev....This package was conflicting with my newly compiled and installed version of Compiz Fusion 0.6.2

Marking this thread as solved. :)

---

