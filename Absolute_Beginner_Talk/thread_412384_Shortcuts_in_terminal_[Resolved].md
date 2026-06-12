---
title: "Shortcuts in terminal [Resolved]"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by kd5gje on 2007-04-18
I have searched the web and can not find a way to make a shortcut in the terminal window.  What I am trying to do is make a shortcut to /etc/init.d/networking in the directory /etc/rc5.d so that my network card will start up with my computer.  Is there a way to make a shortcut from in the terminal?

Thank you.

---

### Post by aysiu on 2007-04-18
```
sudo ln -s /etc/init.d/networking /etc/rc5.d/networking
``` should do it.

---

### Post by jordanmthomas on 2007-04-18
And, for future reference, it's called a symbolic link.  (That way you can look up help if you forget how to do it)

---

### Post by kd5gje on 2007-04-19
Thanks guys.

---

