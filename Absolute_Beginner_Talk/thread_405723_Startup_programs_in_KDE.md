---
title: "Startup programs in KDE?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by miggols99 on 2007-04-10
I want to have Beryl startup automatically. How do I do it?

---

### Post by igknighted on 2007-04-10
I don't know the GUI way to do it, I find the CLI easier anyways:
```
ln -s /usr/bin/beryl-manager ~/.kde/Autostart/
```

make sure you run this as your user, not as root... otherwise it will end up in roots home folder not your users :)

---

### Post by miggols99 on 2007-04-10
Ok thanks :)

---

